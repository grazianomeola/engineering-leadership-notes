# Root-Cause Analysis (RCA) template

*Blameless by design: we look for what in the system, process or tooling allowed the problem to happen, not for who to blame.*

---

## 1. Summary

*Two or three sentences a manager or customer can read in 30 seconds.*

- **What happened:**
- **Impact:**
- **Current status:** Resolved / Mitigated / Under investigation

## 2. Timeline

| Time | Event |
|------|-------|
| | First signal (who or what detected it?) |
| | Escalation |
| | Mitigation in place |
| | Root cause confirmed |
| | Permanent fix released |

**Time to detect:**
**Time to mitigate:**
**Time to fix:**

## 3. Impact

- Who was affected (customers, production, internal teams)?
- How many units, users or builds?
- Safety, security or compliance implications? (Yes/No, with details)

## 4. Root cause

*Ask "why?" until you reach something you can actually change. Usually five times is enough.*

1. Why did it happen?
2. Why?
3. Why?
4. Why?
5. Why?

**Root cause (one sentence):**

**Contributing factors:** *for example timing, configuration, missing test coverage, unclear ownership*

## 5. Why didn't we catch it earlier?

*Often the most valuable section.*

- Which test, review or monitoring step should have caught this?
- Why didn't it?

## 6. Evidence

*Measurements, logs, traces or reproduction steps that confirm the root cause. Hypotheses go here only if clearly marked as such.*

## 7. Actions

| # | Action | Type | Owner | Due date | Status |
|---|--------|------|-------|----------|--------|
| 1 | | Fix | | | |
| 2 | | Prevention | | | |
| 3 | | Detection | | | |

- **Fix:** removes this specific problem.
- **Prevention:** stops the same class of problem from recurring.
- **Detection:** helps us notice it sooner next time.

*Every action has one owner and a date. An action without an owner is a wish.*

## 8. What went well

*What helped us respond? Keep doing it.*

## 9. Lessons learned

*One or two lessons that are useful beyond this incident.*

---

**Author:**
**Reviewed by:**
**Date:**
