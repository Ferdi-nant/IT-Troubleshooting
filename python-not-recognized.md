# Ticket: 'python' Not Recognized / ModuleNotFoundError When Running Script

**Date:** 2026-08-15
**Category:** Software / Environment Configuration
**Status:** Resolved

## 1. Identify the Problem
- Running a Python script (Computer_Specs.py) in VS Code threw:
  `ModuleNotFoundError: No module named 'psutil'`
- Attempted to install the missing module but hit a second error:
  `pip : The term 'pip' is not recognized...`
- Attempted `python -m pip install psutil` instead, which returned:
  `Python was not found; run without arguments to install from the Microsoft Store...`

## 2. Establish a Theory of Probable Cause
Possible causes, ranked by likelihood:
- Windows "App execution alias" for `python` is redirecting to the Microsoft Store instead of the real install
- `pip` and/or Python not added to system PATH during installation
- Multiple Python installs on the system, with VS Code pointing to the wrong one
- Python not actually installed at all

## 3. Test the Theory
- Ran `python --version` and `pip` directly in terminal — both failed, confirming PATH/alias issue
- Tried the alternate Windows launcher command: `py -m pip install psutil`
- This succeeded, confirming a real Python install existed on the system, just not accessible via the `python` command

## 4. Plan and Implement a Solution
- Used `py -m pip install psutil` to install the missing module (bypassing the broken `python` alias)
- Ran the script directly via `py Computer_Specs.py` in the terminal to confirm it worked outside VS Code's Run button
- Checked VS Code's Python interpreter selector (bottom-right corner) to confirm it was pointing to a valid Python install

## 5. Verify Full Functionality
- Ran the script using VS Code's Run button (▶️)
- Script executed successfully and printed system specs with no errors

## 6. Document
- **Root cause:** Windows' `python` command was intercepted by an App Execution Alias pointing to the Microsoft Store, rather than the actual installed Python interpreter. The `py` launcher was unaffected and worked correctly.
- **Fix:** Used `py` instead of `python` to run pip installs and scripts. Confirmed VS Code's interpreter was correctly set.
- **Time to resolve:** ~15 minutes
- **Note for next time:** On Windows, if `python` or `pip` commands fail unexpectedly, try the `py` launcher first before assuming Python isn't installed. If it persists, check Settings → Apps → Advanced app settings → App execution aliases and disable the python.exe/python3.exe Store redirects.