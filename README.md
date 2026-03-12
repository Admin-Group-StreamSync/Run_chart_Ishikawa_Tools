# 📈 GitHub Issues Run Chart Action

Automatically generate a **weekly run chart of GitHub issues created in your repository** and commit the chart back to the repository.

This GitHub Action fetches issue data using the GitHub CLI, processes it with Python, and generates a chart showing the **number of issues created per week**.

The chart is automatically updated on a schedule and committed to the repository.

---

# ✨ Features

- 📊 Generates a **weekly run chart of created issues**
- 🔁 Runs automatically on a **scheduled workflow**
- 🤖 Commits the generated chart back to the repository
- 🐍 Uses **Python + Matplotlib** for visualization
- 🔍 Fetches issue data via the **GitHub CLI**

---

# ⚙️ How It Works

1. The workflow runs on a scheduled cron job.
2. The GitHub CLI retrieves all issues and their creation timestamps.
3. A Python script:
   - Parses the issue creation dates
   - Groups them by week
   - Generates a run chart
4. The generated chart is saved in the repository.
5. The workflow automatically commits the updated chart.

---

# 📅 Workflow Schedule

The workflow runs **every Tuesday at 00:00 UTC**.

```yaml
schedule:
  - cron: '0 0 * * 2'
```

You can modify the cron expression if you want the chart to update more frequently.

---

# 📦 Requirements

Before using this workflow, make sure the following tools are installed:

- **Python 3.12**
- **matplotlib**
- **GitHub CLI (`gh`)**

Install GitHub CLI:  
https://cli.github.com/

---

# 🔧 Initial Setup

Before running the workflow for the first time, you must generate the `issues.json` file.

Run the following command in the root of your repository:

```bash
gh issue list --state all --limit 10000 --json createdAt > IshikawaTools/issues.json
```

This command retrieves all issues and stores their creation timestamps in the JSON file used by the Python script.

---

# 📂 Repository Structure

Example structure:

```
.
├── .github/
│   └── workflows/
│       └── runchart.yml
├── IshikawaTools/
│   ├── runchart_prova.py
│   ├── issues.json
│   └── issue_runchart.png
└── README.md
```

---

# 📊 Generated Output

The action generates a chart showing **issues created per week**.

This helps track **repository activity trends over time**.

---

# 🔐 Permissions

The workflow requires the following permissions:

```yaml
permissions:
  contents: write
  issues: read
```

| Permission | Purpose |
|-------------|--------|
| `issues: read` | Fetch issue creation dates |
| `contents: write` | Commit the generated chart |

---

# 🚀 Use Cases

- Track **repository activity trends**
- Monitor **issue creation velocity**
- Add **lightweight project metrics**
- Visualize repository growth over time

---

# 🛠 Customization

### Change the update schedule

Modify the cron expression in the workflow file.

Example (run daily):

```yaml
cron: '0 0 * * *'
```

---

### Modify the chart appearance

You can edit the Python script:

```
IshikawaTools/runchart_prova.py
```

Possible customizations include:

- line color
- figure size
- grid style
- axis labels
- title formatting

---

# 🤝 Contributing

Contributions, improvements, and suggestions are welcome.

If you find a bug or want to add new features, feel free to open an issue or submit a pull request.

---

# 📄 License

MIT License
