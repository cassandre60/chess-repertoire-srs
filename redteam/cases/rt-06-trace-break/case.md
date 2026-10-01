# Red-team case: rt-06-trace-break

Status: active
Category: weaken-assertion (traceability)
Expected catcher(s): G05 spec traceability

## What the patch does
Deletes the `// SPEC coverage: ...` citation line from
`test/domain/review_scope_test.dart`, leaving the test itself intact.

## Why it is wrong
INV-030 loses its only cited oracle; the spec claims coverage the suite no
longer demonstrates. (Deleting the test instead would be caught by G08; this
case proves G05 watches the mapping itself.)

## Why a naive gate would pass it
The suite is green and no assertion was touched; only the trace check
notices the orphaned invariant.

Patch file: `patch.diff` (git diff format, applies to the commit recorded below)
Recorded against: 21a137d67
