## Unit 7 — Issue selection

**Issue link:** https://github.com/codepath/pathreview-ai201-fa26-howard/issues/60

**Issue title:** Faithfulness checker crashes when a context chunk has `text: None`

**Tier:** [Yes] Tier 1  [No] Tier 2  [No] Tier 3

**Problem summary:**
This issue of Pathreview involves the faithfulness checker and how right now it's `check()` method is assuming that every context chunk's text value is a string when it joins retrieved chunks into a signle context. When a context chunk has `text: None`, the dictionary lookup right now is returning `None` which is causing " ".join(...) to raise a TypeError and prevents evalutuion from completing leading to a crash. Instead of `None`, the lookup should be returning the fallback value. A successful fix would handle `None` text values from chunks correctly in faithfulness_checker.py while preserving regular behavior for already valid text. It would also allow test_none_context_chunk_text to pass.

**Branch name:** fix/60-faithfulness-checker-crashes

**Setup confirmation:** [Yes] App runs locally at localhost:5173

**Cohort ledger:** [Yes] Issue added to cohort ledger
