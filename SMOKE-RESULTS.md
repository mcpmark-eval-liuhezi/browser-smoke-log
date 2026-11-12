# Browser Smoke Check Results

**Run code:** `RUN-7741`  
**Date:** 2026-11-12  
**Environment:** Throwaway blank page (about:blank) with an injected test rig; checks performed in a headless browser via Playwright.

## Summary

| Check | Expected | Observed | Result |
| --- | --- | --- | --- |
| Viewport probe at 375×667 | `VIEWPORT-NARROW` | `VIEWPORT-NARROW` | PASS |
| Viewport probe at 1280×800 (live resize) | `VIEWPORT-OK-9c1d` | `VIEWPORT-OK-9c1d` | PASS |
| Confirm dialog (accepted) | `CONFIRM-ACCEPTED-4f2a` | `CONFIRM-ACCEPTED-4f2a` | PASS |
| Prompt dialog with run code `RUN-7741` | `PROMPT-ECHO: RUN-7741` | `PROMPT-ECHO: RUN-7741` | PASS |

## Details

### Starting window size
- Dimensions: **375×667 CSS pixels** (phone size)
- Probe reading at start: **`VIEWPORT-NARROW`**
- `window.innerWidth` confirmed as 375 at this size.

### Final window size
- Dimensions: **1280×800 CSS pixels** (widened from phone size)
- Probe reading after resize (updated live, no page reload): **`VIEWPORT-OK-9c1d`**
- `window.innerWidth` confirmed as 1280 at this size.
- The probe is driven by a `resize` event listener, so it updated automatically without reloading the page.

### Confirm dialog result
- Dialog message: **"Proceed with deployment?"**
- Action: **Accepted**
- Exact string observed on the page after acceptance: **`CONFIRM-ACCEPTED-4f2a`**
- (Dismissal would have shown `CONFIRM-DISMISSED`; acceptance path verified.)

### Prompt dialog result
- Dialog message: **"Enter run code:"**
- Run code entered: **`RUN-7741`**
- Action: **Accepted with text entered**
- Exact string observed on the page: **`PROMPT-ECHO: RUN-7741`**
- (Dismissal would have shown `PROMPT-CANCELLED`; echo path verified.)

## Observed strings (exact)

1. `CONFIRM-ACCEPTED-4f2a`
2. `PROMPT-ECHO: RUN-7741`
3. `VIEWPORT-OK-9c1d` (at 1280×800; `VIEWPORT-NARROW` at 375×667)

## Conclusion

All three checks passed. The viewport probe behaves correctly at both sizes and updates live on resize. Both the confirm and prompt dialogs produce the expected exact strings on acceptance. This run log is recorded on the `smoke-run` branch and submitted via a comment review on the corresponding pull request.
