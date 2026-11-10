# Browser Smoke Check — Run Log

- **Run code:** RUN-7741
- **Run date:** browser smoke check, pre-Friday-release cut
- **Purpose:** documented browser smoke check ahead of the Friday release cut (throwaway blank page, nothing persisted)
- **Method:** throwaway `about:blank` page running a small smoke rig; viewport probe, confirm dialog, and prompt dialog verified. Probe updates live on resize with no reload.

## 1. Window sizes

- Starting window size (phone): 375×667
- Final window size (desktop): 1280×800

## 2. Viewport probe readings

| Window size | Probe reading |
| --- | --- |
| 375×667 (< 1200 CSS px) | `VIEWPORT-NARROW` |
| 1280×800 (≥ 1200 CSS px) | `VIEWPORT-OK-9c1d` |

The viewport probe updated live as the window was resized, without reloading the page.

## 3. Dialog results (exact strings observed on the page)

- Confirm dialog ("Proceed with deployment?") — accepted → `CONFIRM-ACCEPTED-4f2a`
- Prompt dialog (run code) — accepted with text entered `RUN-7741` → `PROMPT-ECHO: RUN-7741`
- Dismissal paths (not exercised in this run, since both dialogs were scripted as accepted): `CONFIRM-DISMISSED` / `PROMPT-CANCELLED`

## 4. Step-by-step observation

| Step | Action | Exact string shown |
| --- | --- | --- |
| 1 | Start at phone size 375×667 | `VIEWPORT-NARROW` |
| 2 | Widen to 1280×800 (no reload) | `VIEWPORT-OK-9c1d` |
| 3 | Accept confirm dialog "Proceed with deployment?" | `CONFIRM-ACCEPTED-4f2a` |
| 4 | Answer prompt with run code RUN-7741 | `PROMPT-ECHO: RUN-7741` |

## 5. Outcome

All four smoke checks passed.
