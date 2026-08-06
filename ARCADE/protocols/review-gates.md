# Protocol: Review Gates

The Blind Spot Reviewer should run at meaningful gates, not after every tiny edit.
The Profile Reviewer is separate: run it explicitly or when repeated evidence
shows that guidance or routing no longer matches the user. It should not run at
every gate or infer a profile change from a single task.

## Gates

- After concept brief
- After document selection
- After technical architecture
- After art/UX direction
- After pre-production plan
- After production slices
- Before production execution
- Before release

## Review placement

Small/local review:

- Add directly to the reviewed document under `Review Notes`.

Large/cross-domain review:

- Add to `/docs/reviews/`.

## Judgment values

- Approved
- Approved with warnings
- Blocked until changes
- Needs human decision
