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


## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
I have sucessfully run the project and identified the problem area

**Next steps:**
I want to work on the tests and make sure that my project is ready for my PR

**Blockers:**
I came across CI issues regarding the unit tests, the Linter is being too strict for these tests and forcing all test functions to have a return value, for now I am following the linter

---

### Check-in 2 (end of week)

**PR link:** https://github.com/ascherj/pathreview/pull/857 

**Branch:** fix/64-newline-sanitization-in-user-supplied-text

**What you built:**
I have updated the sanitizer function in safety/prompt_defense.py to properly sanitize away newline characters. I have also added unit tests to test the new functionality of the sanitizer function

**Tests added or updated:**
I added new tests that cover all of the injection patters covered in the initial Issue,  such as `\n---\n` and `\nSystem:`


**Self-review confirmation:** [X] make check passes  [X] make test-unit passes

**Draft PR feedback received from:** "none"
