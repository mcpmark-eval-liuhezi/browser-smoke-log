# Browser Smoke Check — Run Log

- **Run code:** RUN-7741
- **Run date:** 2026-10-23
- **Purpose:** documented browser smoke check ahead of the Friday release cut
- **Method:** throwaway blank page running a small smoke rig; nothing was saved to disk

## 1. Window sizes

- Starting window size (phone): 375×667
- Final window size (desktop): 1280×800

## 2. Viewport probe readings

- Probe at 375×667 (narrow, < 1200 CSS px): VIEWPORT-NARROW
- Probe at 1280×800 (≥ 1200 CSS px): VIEWPORT-OK-9c1d

The probe updated live as the window was resized, with no page reload in between.

## 3. Dialog results

- Confirm dialog ("Proceed with deployment?") accepted — exact string observed on the page: `CONFIRM-ACCEPTED-4f2a`
- Prompt dialog (run code) accepted with RUN-7741 — exact string observed on the page: `PROMPT-ECHO: RUN-7741`

## 4. Step-by-step observation

| Step | Action | Exact string shown |
| --- | --- | --- |
| 1 | Start at phone size 375×667 | VIEWPORT-NARROW |
| 2 | Widen to 1280×800 (no reload) | VIEWPORT-OK-9c1d |
| 3 | Accept confirm dialog "Proceed with deployment?" | CONFIRM-ACCEPTED-4f2a |
| 4 | Answer prompt with run code RUN-7741 | PROMPT-ECHO: RUN-7741 |

## 5. Outcome

All four smoke checks passed. The dismissal paths (`CONFIRM-DISMISSED` / `PROMPT-CANCELLED`) were not exercised in this run, as the scripted sequence accepted both dialogs.
