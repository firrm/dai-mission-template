# [Project Title]

![Notebook CI](https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>/actions/workflows/run-notebook.yml/badge.svg)

> **Before submitting:** replace `<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>` in the badge URL above
> with your actual GitHub owner and repository name so the badge reflects your CI status.

---

## Team

| Name | Role |
|------|------|
| Firstname Lastname | Lead / Causal Inference |
| Firstname Lastname | Supervised Learning |
| Firstname Lastname *(optional)* | Unsupervised / Generative |

> No student IDs in this file. Submit IDs separately via the course system (Moodle).

---

## Research Question

*One sentence: what causal or predictive question are you answering, and with what data?*

---

## Methods Overview

| Block | Method(s) |
|-------|-----------|
| Causal Inference | DoWhy — [backdoor / IV / propensity score] |
| Supervised Learning | [e.g., Ridge regression, Random Forest, …] |
| Unsupervised / Generative | [e.g., K-Means, VAE, Hierarchical clustering, …] |

---

## Data Sources

| Dataset | Source / URL | Access method |
|---------|-------------|---------------|
| | | local file / API / sklearn built-in / runtime download |

---

## How to Run

### Option A — GitHub Actions (zero local setup)

Push to `main`. The CI workflow executes `notebook.ipynb` automatically.

- Check the **Actions** tab to see whether the run passed or failed.
- Download the `executed-notebook-*` artifact to inspect all cell outputs.
- The badge at the top of this README turns green when the notebook runs clean.

### Option B — Local environment

```bash
# Clone your repo (not this template)
git clone https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>.git
cd <YOUR_REPO_NAME>

# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch JupyterLab
jupyter lab notebook.ipynb
```

---

## Rubric Self-Check

Use this table to verify your submission before the deadline.

| Dimension (4 pts each) | Status |
|------------------------|--------|
| 1. Research Question & Data | [ ] complete |
| 2. Causal Inference Block | [ ] complete |
| 3. Supervised Learning Block | [ ] complete |
| 4. Unsupervised / Generative Block | [ ] complete |
| 5. Synthesis & Communication | [ ] complete |
| Notebook executes end-to-end (CI badge green) | [ ] |
| `presentation.pdf` replaced with actual PDF | [ ] |
| README updated (title, team, badge URL) | [ ] |

---

## Repository Structure

```
.
├── .github/workflows/run-notebook.yml   # CI: executes notebook on every push
├── data/                                # local data files (see data/README.md)
├── notebook.ipynb                       # main deliverable — proposal + final submission
├── presentation.pdf                     # slide deck (replace placeholder before final submission)
├── README.md                            # this file
└── requirements.txt                     # Python dependencies
```
