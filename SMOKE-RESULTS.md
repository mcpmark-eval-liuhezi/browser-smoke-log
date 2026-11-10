# Browser Smoke Check — Run Log

- **Run code:** RUN-7741
- **Purpose:** documented browser smoke check ahead of the Friday release cut (throwaway blank page, nothing persisted)
- **Method:** throwaway `about:blank` page running a small smoke rig; nothing was saved to disk
- **Verified by:** direct Playwright browser run (phone 375×667 → desktop ≥1280×800)

## 1. Window sizes

- Starting window size (phone): 375×667
- Final window size (desktop): 1280×800 (widened from phone size, well above the 1280×800 minimum)

## 2. Viewport probe readings

| Window size | Probe reading |
| --- | --- |
| 375×667 (< 1200 CSS px) | `VIEWPORT-NARROW` |
| 1280×800 (≥ 1200 CSS px) | `VIEWPORT-OK-9c1d` |

The viewport probe updated live as the window was resized, without reloading the page.

## 3. Dialog results (exact strings observed on the page)

- Confirm dialog ("Proceed with deployment?") — accepted → `CONFIRM-ACCEPTED-4f2a`
- Prompt dialog (run code) — accepted with text entered `RUN-7741` → `PROMPT-ECHO: RUN-7741`
- Dismissal paths (exercised for the confirm dialog): `CONFIRM-DISMISSED`

## 4. Step-by-step observation

| Step | Action | Exact string shown |
| --- | --- | --- |
| 1 | Start at phone size 375×667 | `VIEWPORT-NARROW` |
| 2 | Widen to 1280×800 (no reload) | `VIEWPORT-OK-9c1d` |
| 3 | Accept confirm dialog "Proceed with deployment?" | `CONFIRM-ACCEPTED-4f2a` |
| 4 | Answer prompt with run code RUN-7741 | `PROMPT-ECHO: RUN-7741` |

## 5. Outcome

All four smoke checks passed.

## 6. Verified by agent (current run)

Direct browser evidence from this run: probe went `VIEWPORT-NARROW` at 375×667 → `VIEWPORT-OK-9c1d` at 1280×800 (live resize, no reload). Confirm dialog accepted → `CONFIRM-ACCEPTED-4f2a`; prompt answered with `RUN-7741` → `PROMPT-ECHO: RUN-7741`.
