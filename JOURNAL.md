## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/64

**Issue title:** Prompt injection defense doesn't sanitize newline characters in user-supplied resume text

**Tier:** [ ] Tier 1  [X] Tier 2  [ ] Tier 3

**Problem summary:**
In `safety/prompt_defense.py`, the input sanitizer doesn't properly sanitize away newline characters. Currently, it does successfully strips `>, <, and {}` but misses the newline escape sequence like this: `\n---\n` and `\nSystem:`. Successfuly fixing this requires me to change how the santizer handles user input, so that it actually strips out these unwanted characters 

**Branch name:** `fix/64-newline-sanitization-in-user-supplied-text`

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** https://github.com/Tohny123/pathreview/commit/8ea9eaf1fed2c2c667a03889f1599a6e9cc952ca

**Reproduction summary:**
First, I looked at where the "sanitize" function was implemented, but there were no implementations running in the flask API, so I decided to run the function directly via a new file called `reproduction.py`. When I ran this file, I noticed that the file did sanitize "<" and ">" chars

**PLAN.md link:** https://github.com/Tohny123/pathreview/blob/fix/64-newline-sanitization-in-user-supplied-text/PLAN.md

**Walkthrough video (recommended):** 

**Blockers or open questions:**
