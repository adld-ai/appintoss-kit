# Development Verification Loop

This is the mandatory execution path for implementation work.

## Exact Loop

```text
1. Develop the smallest scoped change.
2. Verify with an adversarial verifier as a design rule.
3. Run focused static/build/unit checks.
4. Run E2E for user-visible behavior.
5. If any check fails:
   a. Stop feature expansion.
   b. Capture the failing command and output.
   c. Identify the root cause before editing.
   d. Replan the smallest corrective change.
   e. Implement the fix.
   f. Rerun the same failing command.
   g. Rerun the relevant broader checks.
6. Only when checks pass, move to the next step.
```

## Required Verification Path

Use this path for every feature, bugfix, or UI change:

1. **Local requirement check**
   - Re-read the user request.
   - Re-read the relevant `guide/*.md` files.
   - Define the success criteria before editing.

2. **Development**
   - Read the target code first.
   - Make the smallest correct change.
   - Avoid adjacent cleanup unless required.

3. **Adversarial design verifier**
   - Use [`design-system.md`](design-system.md) as the design rule.
   - Try to reject the work before accepting it.
   - Ask:
     - Does the main user task have a clear next action?
     - Did the change add choices or inputs that can be removed?
     - Are empty, loading, success, error, edit, delete, and recovery states
       handled where the flow can reach them?
     - Is status communicated without relying on color alone?
     - Does text fit without overlap on mobile and desktop?
     - Is the copy truthful, concrete, and aligned with implemented behavior?
     - Are only the approved Toss palette colors used?
   - If any answer fails, replan before continuing.

4. **Focused checks**
   - Run the narrowest relevant command first.
   - Prefer exact project scripts when available:
     - `npm run lint`
     - `npm run build`
     - `npm test`
     - `npm run test`
   - If a script does not exist, report that exact fact and use the closest
     available check.

5. **E2E check**
   - For browser-visible behavior, run the project E2E command if present:
     - `npm run test:e2e`
     - `npm run e2e`
     - `npx playwright test`
   - If no E2E setup exists, run the app and perform a browser verification
     path with Playwright or the available browser automation tool.
   - Capture the tested URL, viewport, scenario, and result.

6. **Failure handling**
   - Do not patch blindly after a failing E2E.
   - Record:
     - failing command
     - failing scenario
     - expected behavior
     - actual behavior
     - root cause file/function/state
     - smallest replan
   - Fix only the root cause.
   - Rerun the same failing E2E first.
   - Then rerun the broader relevant checks.

7. **Pass gate**
   - Move to the next step only after the relevant checks pass.
   - If verification cannot be run, state the blocker and residual risk.
   - Never claim completion from code inspection alone.

## Root Cause Replan Template

Use this template when a check fails:

```markdown
Failure evidence:
- Command:
- Scenario:
- Expected:
- Actual:

Root cause:
- File/function:
- Why this causes the failure:

Replan:
- Smallest fix:
- Same failing command to rerun:
- Broader checks to rerun after that:
```

## Design Verifier Output Template

```markdown
Adversarial design verification:
- Main task clarity:
- Action count reduced or justified:
- State coverage:
- Accessibility and non-color status:
- Copy truthfulness:
- Toss palette compliance:
- Verdict: pass / fail
```
