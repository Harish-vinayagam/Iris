<div align="center">

<h1>🌿 Iris</h1>

<p><strong>Open-Source Sustainability Index</strong></p>

<p>
  <a href="https://github.com/your-username/iris/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT" />
  </a>
  <a href="https://github.com/your-username/iris/actions">
    <img src="https://img.shields.io/github/actions/workflow/status/your-username/iris/ci.yml?label=CI" alt="CI Status" />
  </a>
  <img src="https://img.shields.io/badge/Built%20at-FOSS%20Hack%202026-green" alt="FOSS Hack 2026" />
  <img src="https://img.shields.io/badge/Stack-React%20%7C%20Node%20%7C%20Express-informational" alt="Stack" />
</p>

<p><em>Evaluate the long-term health and reliability of any GitHub repository — transparently, locally, and for free.</em></p>

</div>

---

## Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [What Iris Does](#what-iris-does)
- [Sustainability Index Model](#sustainability-index-model)
- [Repository Activity Heatmap](#repository-activity-heatmap)
- [System Architecture](#system-architecture)
- [Tech Stack](#tech-stack)
- [API Reference](#api-reference)
- [Getting Started](#getting-started)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

Modern software depends heavily on open-source projects. Yet there is no structured, transparent way to assess whether a repository is actively maintained, community-supported, or at risk of abandonment.

**Iris** transforms raw GitHub repository data into a clear, explainable **Sustainability Score (0–100)** — helping developers and organizations make informed decisions about the projects they depend on.

> Iris does not use proprietary AI models or closed APIs. All scoring logic runs locally and is fully documented.

---

## Problem Statement

Open-source ecosystems face recurring sustainability challenges:

| Problem | Description |
|---|---|
| 🔥 Maintainer burnout | Core contributors stepping away without successors |
| 🪦 Project abandonment | Repositories silently going unmaintained |
| 🚌 High bus-factor risk | Single contributor dominance creating fragility |
| 🐌 Stale issues & slow PRs | Signals of reduced responsiveness |
| 🕵️ Hidden dependency risks | Widely-used packages with no health visibility |

GitHub exposes raw metrics but does not interpret them. Developers manually inspect repositories to judge reliability — leading to **inconsistent and subjective decisions**.

Iris solves this by providing a **structured, reproducible sustainability index**.

---

## What Iris Does

Given any GitHub repository URL, Iris:

- 📊 Analyzes recent commit activity and development consistency
- ⚡ Evaluates maintainer responsiveness via issue and PR metrics
- 👥 Measures contributor diversity and participation
- 🚨 Detects sustainability risks — bus factor, contribution concentration
- 🧹 Checks structural hygiene — license, docs, CI, tests
- 🔢 Generates a **weighted sustainability score (0–100)**
- 🗓️ Visualizes activity patterns using a commit heatmap
- 💬 Provides clear, human-readable risk explanations

---

## Sustainability Index Model

The overall score is computed across **five evaluation dimensions**:

```
Final Score =
  (Activity            × 30%) +
  (Responsiveness      × 25%) +
  (Community Strength  × 20%) +
  (Sustainability Risk × 15%) +
  (Project Hygiene     × 10%)
```

Each component produces a normalized score from **0 to 100**.

<details>
<summary><strong>1. Activity (30%)</strong></summary>

- Commits in the last 90 days
- Recency of last commit
- Activity consistency ratio
- Inactive streak detection

</details>

<details>
<summary><strong>2. Responsiveness (25%)</strong></summary>

- Average pull request merge time
- Issue closure rate
- Percentage of stale issues

</details>

<details>
<summary><strong>3. Community Strength (20%)</strong></summary>

- Total number of contributors
- Active contributors in the last 90 days
- Contributor distribution across the codebase

</details>

<details>
<summary><strong>4. Sustainability Risk (15%)</strong></summary>

- Bus factor detection
- Contribution concentration ratio

</details>

<details>
<summary><strong>5. Project Hygiene (10%)</strong></summary>

- License presence
- README availability
- Contributing guidelines
- CI configuration
- Test structure

</details>

---

## Repository Activity Heatmap

Iris includes a **repository-level commit heatmap** — similar to GitHub's contribution grid — that visualizes:

- Daily commit frequency
- Activity consistency over time
- Longest inactive streak
- Peak development periods

This heatmap feeds directly into the **Activity Score** calculation and is rendered interactively in the frontend.

---

## System Architecture

```
Client (React + Vite)
        │
        ▼
Backend API (Node.js + Express)
        │
        ▼
GitHub REST API
        │
        ▼
Scoring Engine (local, transparent)
        │
        ▼
Sustainability Report
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React (Vite), Tailwind CSS, Recharts, Custom Heatmap Grid |
| **Backend** | Node.js, Express, Axios |
| **Config** | dotenv |
| **DevOps** | Docker (optional), GitHub Actions (CI), ESLint, Prettier |

---

## API Reference

### `POST /api/analyze`

**Request body:**

```json
{
  "repoUrl": "https://github.com/user/repo"
}
```

**Response:**

```json
{
  "overallScore": 74,
  "activityScore": 80,
  "responsivenessScore": 70,
  "communityScore": 60,
  "riskScore": 65,
  "hygieneScore": 90,
  "riskAlerts": [
    "High bus factor detected",
    "PR merge time above threshold"
  ],
  "heatmapData": {}
}
```

---

## Getting Started

### Prerequisites

- Node.js ≥ 18
- A [GitHub Personal Access Token](https://github.com/settings/tokens) (for API access)

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/iris.git
cd iris
```

### 2. Setup the Backend

```bash
cd server
npm install
```

Create a `.env` file inside `server/`:

```env
GITHUB_TOKEN=your_github_personal_access_token
```

Start the backend server:

```bash
npm run dev
```

### 3. Setup the Frontend

```bash
cd client
npm install
npm run dev
```

The app will be available at `http://localhost:5173`.

---

## Roadmap

- [ ] Dependency risk analysis
- [ ] GitHub Action integration for automated scoring
- [ ] Repository comparison mode
- [ ] Historical score tracking over time
- [ ] Exportable PDF reports
- [ ] Public API version

---

## Contributing

Contributions are welcome and appreciated.

Please read [`CONTRIBUTING.md`](CONTRIBUTING.md) before submitting a pull request.

> All scoring logic improvements must include documented reasoning explaining the rationale behind metric weights or thresholds.

---

## License

Licensed under the [MIT License](LICENSE).

---

<div align="center">
  <sub>Built with ❤️ during <strong>FOSS Hack 2026</strong></sub>
</div>