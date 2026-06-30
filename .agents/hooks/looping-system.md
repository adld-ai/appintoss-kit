# Looping System Hook

This hook binds the resolver system to every development step.

## `pre-task-resolve`

Before acting:

1. Read root `AGENTS.md`.
2. Read `guide/resolver.md`.
3. Resolve all matching routes.
4. Read all resolved guide files.
5. If the task changes agent behavior, skills, hooks, or guide files, resolve
   `AGENT_RULES`.

## `pre-edit-gate`

Before editing:

1. State the smallest scoped change.
2. Identify verification commands or scans that can prove the change.
3. For UI/copy/assets, run the adversarial design verifier mentally against
   `guide/design-system.md` before changing files.

## `post-edit-verify`

After editing:

1. Run the narrowest relevant check first.
2. Run broader resolved checks.
3. For visible behavior, run E2E or browser verification when available.
4. For documentation or agent setup, verify paths, route names, forbidden stale
   references, and required keywords.

## `failure-replan`

When any check fails:

```text
fail
-> stop expansion
-> capture command and output
-> identify root cause
-> replan smallest fix
-> fix only root cause
-> rerun the same failing check
-> rerun broader resolved checks
-> only then move forward
```

## `pre-completion-evidence`

Before claiming completion:

1. Identify the claim.
2. Identify the command or scan that proves it.
3. Run it fresh.
4. Read output and exit code.
5. Report evidence and any residual risk.
