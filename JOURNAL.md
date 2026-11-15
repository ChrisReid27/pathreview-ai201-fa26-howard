## Unit 7 — Issue selection

**Issue link:** https://github.com/codepath/pathreview-ai201-fa26-howard/issues/60

**Issue title:** Faithfulness checker crashes when a context chunk has `text: None`

**Tier:** [Yes] Tier 1  [No] Tier 2  [No] Tier 3

**Problem summary:**
This issue of Pathreview involves the faithfulness checker and how right now it's `check()` method is assuming that every context chunk's text value is a string when it joins retrieved chunks into a signle context. When a context chunk has `text: None`, the dictionary lookup right now is returning `None` which is causing " ".join(...) to raise a TypeError and prevents evalutuion from completing leading to a crash. Instead of `None`, the lookup should be returning the fallback value. A successful fix would handle `None` text values from chunks correctly in faithfulness_checker.py while preserving regular behavior for already valid text. It would also allow test_none_context_chunk_text to pass.

**Branch name:** fix/60-faithfulness-checker-crashes

**Setup confirmation:** [Yes] App runs locally at localhost:5173

**Cohort ledger:** [Yes] Issue added to cohort ledger


## Unit 8 — Reproduction & solution planning

**Note: steps to reproduce the bug issue**:

1. Install dependenicies with `.venv\Scripts\python.exe -m pip install -e ".[dev]"`.
2. Reproduce the bug with `.venv\Scripts\python.exe -c "from rag.evaluator.faithfulness_checker import FaithfulnessChecker; FaithfulnessChecker().check('Knows Python.', [{'text': None}])"`.
3. After that gets run, the type error message will get returned: `TypeError: sequence item 0: expected str instance, NoneType found`.
4. Run the dedicated test for this issue from the unittest folder: `.venv\Scripts\python.exe -m pytest tests/unit/test_faithfulness_checker.py::TestFaithfulnessChecker::test_none_context_chunk_text -q`. This test will return `xfailed` becuase the test is marked as expected to fail.

**Reproduction commit link:** [link to commit documenting the reproduced issue]

**Reproduction summary:**
[1–2 sentences: How did you reproduce the issue? What did you observe?]

**PLAN.md link:** [link to PLAN.md in your fork]

**Walkthrough video (recommended):** [link to your Loom video, ≤2 min — recommended, not graded]

**Blockers or open questions:**
[Anything you're still uncertain about going into Unit 9, or leave blank]