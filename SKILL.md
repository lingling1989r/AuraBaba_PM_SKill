---
name: auramanager-platform
description: "Use when a user wants to operate 灵光爸爸 itself through the built-in platform skill. Teaches direct bearer-token HTTP access to 灵光爸爸 backend APIs for issue and calendar work, workspace routing via X-Workspace-Slug with X-Workspace-ID compatibility, personal access token setup, and the API surface for listing, creating, updating, assigning, commenting on, labeling, and deleting issues plus creating, updating, listing, and deleting calendar events."
user-invocable: false
allowed-tools: 
---

# 灵光爸爸 Platform

Use this skill when the user wants an agent to interact with 灵光爸爸 itself as a
platform capability, not through the 灵光爸爸 CLI.

Every claim below is traced to source in
`references/auramanager-platform-source-map.md`. When in doubt, read that file.

## The invariant

This platform skill talks to the 灵光爸爸 backend HTTP API directly with bearer
token authentication. It does not require the 灵光爸爸 CLI, shell access, or a
local runtime helper.

Send the personal access token as a bearer token:

```http
Authorization: Bearer <personal-access-token>
```

For normal callers, route the workspace with `X-Workspace-Slug` first. Keep
`X-Workspace-ID` compatibility for callers that already know the UUID.

```http
X-Workspace-Slug: <workspace-slug>
X-Workspace-ID: <workspace-uuid>
```

Resolution order for non-task-token requests is:

1. middleware-injected workspace context
2. `X-Workspace-Slug`
3. `?workspace_slug=`
4. `X-Workspace-ID`
5. `?workspace_id=`

Task-token requests are different: when `X-Actor-Source: task_token` is present,
`X-Workspace-ID` wins immediately because the task token is already bound to a
workspace.

## Personal access tokens

灵光爸爸 personal access tokens are created from Settings -> API Tokens and are
managed through `/api/tokens`.

Available endpoints:

```text
GET    /api/tokens
POST   /api/tokens
POST   /api/tokens/current/renew
DELETE /api/tokens/{id}
```

Token creation returns the plaintext token only once in the create response. After
that, list responses expose metadata such as the token prefix, expiry, and last-used
timestamps, but not the raw token value.

Practical consequence:

- Copy the plaintext token immediately after creation.
- If another agent should use the 灵光爸爸 platform skill, create a separate
token for that agent instead of reusing the user's long-lived token.

## Issue API surface

The skill covers direct 灵光爸爸 issue operations through `/api/issues`.

Available endpoints:

```text
GET    /api/issues/search
GET    /api/issues/child-progress
GET    /api/issues/children
GET    /api/issues/grouped
GET    /api/issues
POST   /api/issues
GET    /api/issues/{id}
PUT    /api/issues/{id}
DELETE /api/issues/{id}
GET    /api/issues/{id}/comments
POST   /api/issues/{id}/comments
GET    /api/issues/{id}/timeline
GET    /api/issues/{id}/children
GET    /api/issues/{id}/attachments
GET    /api/issues/{id}/labels
POST   /api/issues/{id}/labels
DELETE /api/issues/{id}/labels/{labelId}
GET    /api/issues/{id}/metadata
PUT    /api/issues/{id}/metadata/{key}
DELETE /api/issues/{id}/metadata/{key}
GET    /api/issues/{id}/pull-requests
```

Current issue payloads include fields such as:

- `id`, `workspace_id`, `number`, `identifier`, `title`, `description`
- `status`, `priority`
- `assignee_type`, `assignee_id`
- `creator_type`, `creator_id`
- `parent_issue_id`, `project_id`
- `start_date`, `due_date`
- `metadata`, `attachments`, `labels`, `reactions`

Current valid issue status values are:

```text
backlog, todo, in_progress, in_review, done, blocked, cancelled
```

Current valid issue priority values are:

```text
urgent, high, medium, low, none
```

Assignees are polymorphic. To assign an issue, send both `assignee_type` and
`assignee_id`. The assignee may be a member or an agent; do not assume every
assignee is a human user.

## Calendar API surface

The platform skill also includes calendar scheduling. It can list, create, update,
and delete calendar events through the backend API directly.

Available endpoints:

```text
GET    /api/calendar/events
POST   /api/calendar/events
PUT    /api/calendar/events/{id}
DELETE /api/calendar/events/{id}
```

So yes: calendar event creation is part of the 灵光爸爸 platform skill's intended
surface.

## Minimal direct-call examples

List issues in a workspace:

```http
GET /api/issues
Authorization: Bearer <personal-access-token>
X-Workspace-Slug: <workspace-slug>
```

Create an issue assigned to an agent or member:

```json
{
  "title": "Review the release checklist",
  "status": "todo",
  "priority": "medium",
  "assignee_type": "agent",
  "assignee_id": "<agent-or-member-id>"
}
```

Create a calendar event:

```http
POST /api/calendar/events
Authorization: Bearer <personal-access-token>
X-Workspace-Slug: <workspace-slug>
Content-Type: application/json
```

## Incorrect -> correct

Incorrect: teaching the platform skill as a CLI wrapper.

```text
aura issue list
aura issue create
```

Those are CLI commands, not the contract this platform skill should teach.

Correct: direct backend HTTP requests authenticated with a bearer token and routed to
the target workspace.

```http
Authorization: Bearer <personal-access-token>
X-Workspace-Slug: <workspace-slug>
GET /api/issues
POST /api/calendar/events
```

## References

- `references/auramanager-platform-source-map.md` — every behavior above mapped to
  `file:line` in `server/`, plus verification commands to re-derive the lines.
