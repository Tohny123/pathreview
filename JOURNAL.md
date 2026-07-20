## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/64

**Issue title:** Prompt injection defense doesn't sanitize newline characters in user-supplied resume text

**Tier:** [ ] Tier 1  [X] Tier 2  [ ] Tier 3

**Problem summary:**
In `safety/prompt_defense.py`, the input sanitizer doesn't properly sanitize away newline characters. Currently, it does successfully strips `>, <, and {}` but misses the newline escape sequence like this: `\n---\n` and `\nSystem:`. Successfuly fixing this requires me to change how the santizer handles user input, so that it actually strips out these unwanted characters 

**Branch name:** `fix/64-newline-sanitization-in-user-supplied-text`

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger