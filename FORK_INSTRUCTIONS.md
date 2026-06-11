# How to Start Your DAI Mission from This Template

## Why "Use this template" and not "Fork"?

| | "Use this template" | Fork |
|-|---------------------|------|
| Commit history | Fresh single commit | Full history of the template |
| Connection to template | None — fully independent | Linked; PRs back to template are possible |
| Naming | Your choice | Shows "forked from firrm/dai-mission-template" |

For academic submissions, **"Use this template"** is cleaner: no accidental pull
requests back to the instructor's repository, and each team has an independent history.

---

## Step 1 — Create your team's repository

1. Go to **https://github.com/firrm/dai-mission-template**
2. Click the green **"Use this template"** button (top right of the repo page)
3. Select **"Create a new repository"**
4. Set the **owner** to one team member's GitHub account
5. Set the **repository name** — use the convention: `dai-mission-ss26-team-NN`
   (replace `NN` with your team number, e.g. `dai-mission-ss26-team-07`)
6. Set visibility to **Public**  
   *(required: the CI badge is only visible to unauthenticated viewers — including
   graders — when the repo is public)*
7. Click **"Create repository from template"**

---

## Step 2 — Invite your teammates

Go to **Settings → Collaborators → Add people** and search by GitHub username.  
All team members need **Write** access.

---

## Step 3 — Update the README

Open `README.md` and:

- Replace `[Project Title]` with your actual project title
- Fill in the **Team** table (names and roles — no student IDs in this file)
- **Update the CI badge URL**: change `<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>`
  to your actual owner/repo name, e.g.:
  ```
  ![Notebook CI](https://github.com/jsmith/dai-mission-ss26-team-07/actions/workflows/run-notebook.yml/badge.svg)
  ```
- Fill in the **Research Question**, **Methods Overview**, and **Data Sources** tables

---

## Step 4 — Work in the notebook

1. Open `notebook.ipynb` in JupyterLab (or push and use GitHub's notebook preview)
2. Read the **`[TEMPLATE]`** markdown cells — they explain what's expected in each section
3. Replace the **`[EXAMPLE — replace with your analysis]`** code cells with your own analysis
4. Keep the section structure (§1–§5) — graders navigate by section

**Proposal stage:** complete Sections 1–6 (Research Question through Work Plan).  
**Final stage:** complete all sections including Results and Discussion.

---

## Step 5 — Commit and push

```bash
git add notebook.ipynb README.md
git commit -m "feat: add team info and initial research question"
git push origin main
```

The CI workflow starts automatically. Check the **Actions** tab — a green check
means the notebook runs end-to-end without errors.

---

## Step 6 — Proposal submission

Submit your repository URL in the course system (Moodle) as your proposal.  
The proposal is approved once the instructor confirms Sections 1–6 are complete
and the research question is accepted. Feedback is given within one week.

---

## Step 7 — Final submission

1. Replace `presentation.pdf` with your actual presentation PDF (keep the same filename)
2. Confirm the CI badge is **green** (notebook runs clean)
3. Submit the repository URL as your final deliverable in the course system

---

## Troubleshooting

**CI is failing (red badge)**

1. Click the failing workflow run in the **Actions** tab
2. Expand the **"Execute notebook"** step
3. Read the Python traceback — the cell number and error message are shown

Common causes and fixes:

| Symptom | Fix |
|---------|-----|
| `ModuleNotFoundError: No module named 'X'` | Add `X` to `requirements.txt` and push |
| `FileNotFoundError: data/myfile.csv` | Either commit the file (see `data/README.md`) or download it in the notebook |
| `TimeoutError` (cell ran > 600 s) | Reduce dataset size or number of epochs for CI; add a comment explaining the trade-off |
| `KeyError` / `AttributeError` | Likely a library version mismatch — pin the version in `requirements.txt` |

**Badge shows "unknown"**

- No workflow has run yet: push a commit to `main` to trigger the first run
- Repo is private: badge always shows "unknown" to unauthenticated viewers — keep the repo public

**Badge not updating after a successful run**

GitHub CDN caches badge images for up to 5 minutes. Hard-refresh the README page
(`Ctrl+Shift+R` / `Cmd+Shift+R`).

**Large data file rejected by GitHub (> 100 MB)**

See `data/README.md` for alternatives (runtime download, API access, Git LFS).

---

## Adding heavier dependencies (TensorFlow, PyTorch, etc.)

If your generative block uses a deep learning framework, add it to `requirements.txt`:

```
tensorflow>=2.17.0
# or
torch>=2.3.0
torchvision>=0.18.0
```

Be aware this adds 2–5 minutes to CI install time on a cold runner. The pip cache
(`cache: "pip"` in the workflow) means subsequent pushes are much faster if
`requirements.txt` has not changed.
