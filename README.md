# SkillSphere AI

A colourful, single-page career dashboard for B.Tech students. Answer a short skills assessment, then get a personal roadmap, skill-gap report, project ideas, teammate matches, hackathon search links, a portfolio preview and interview practice. Everything runs in the browser. There is no backend and no build step.

![Dashboard on desktop](screenshots/dashboard-desktop.png)

## Features

| Feature | What it does |
| --- | --- |
| **Step-by-step sign-up** | Asks for name, password, B.Tech year, city and weekly study hours. Then you pick a major area (Core CS, Web development or AI and data), then a role in that area, and only then rate the 5–7 skills that role needs. The dashboard opens once everything is answered. |
| **Dashboard** | Readiness score ring, steps done, skill gaps, projects built, estimated weeks to goal, next action, opportunities and a year-wise plan. |
| **Skill roadmap** | One step per missing skill level, biggest gaps first, plus a plan for your academic year. Ticking a step raises that skill level and updates the whole app. |
| **Learn & notes** | Four short study notes per skill with YouTube links (direct videos for Python, C++, HTML, CSS, JavaScript and SQL, search links for the rest) and a Hindi search link. |
| **Skill gap detector** | Sliders show your level against what the chosen role expects. |
| **Project recommender** | Ranks project ideas by how many of your gaps they close. |
| **Team match** | Scores sample teammates by how well their strengths cover your gaps. |
| **Hackathon finder** | Live Google, Unstop, Devfolio and Reskilll searches for your city, plus verified listings. |
| **Portfolio builder** | Live preview from your name, bio, strong skills and built projects. |
| **Interview practice** | Five questions with keyword and length-based feedback. |
| **Accounts and progress** | Several local accounts per browser, saved progress, log in and log out. |
| **Role completion** | At 100% readiness you see a "You're ready" card. Choose a new role and the form reopens. Completed roles are kept. |

Career goals: Software Engineer Intern, Full-Stack Developer, AI/ML Engineer, Frontend Developer, Backend Developer, Data Analyst, Data Scientist, Product Company SDE and Systems Engineer.

## Screenshots

| Sign-up form | Mobile dashboard |
| --- | --- |
| ![Sign-up form](screenshots/signup-form.png) | ![Mobile dashboard](screenshots/dashboard-mobile.png) |

## Run locally

No install needed. Open `index.html` in a browser. To serve it instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy on GitHub Pages

1. Create a new repository, for example `skillsphere-ai`, and upload `index.html`, `README.md`, `LICENSE` and the `screenshots/` folder.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. After a minute your app is live at `https://<your-username>.github.io/skillsphere-ai/`.

## How it works

- **Readiness** = sum of `min(your level, required level)` divided by the sum of required levels, for the chosen role.
- **Roadmap steps** are created from your starting levels. Each completed step adds one level to that skill, so progress carries across roles.
- **Recommendations** (projects, team match, opportunities) are rule-based scores. There is no language model and no network call for the "AI" features.

## Data and privacy

- Accounts and progress are stored in your browser's `localStorage`. Passwords are salted and hashed with SHA-256 using the Web Crypto API.
- This is a convenience lock, not secure authentication. Anyone with access to the browser profile can read or delete the stored data. Clearing browser data deletes accounts, and a forgotten password cannot be recovered.
- Nothing is sent to a server. External links (YouTube, Google, Unstop and others) open in a new tab.

## Customise

All data lives at the top of the `<script>` in `index.html`:

| Constant | Purpose |
| --- | --- |
| `R` | Career goals and the skill levels each role expects |
| `N` | Study notes and video links per skill |
| `Y` | Year 1–4 milestones |
| `P` | Project ideas and the skills they train |
| `T` | Sample teammates |
| `H` | Verified hackathon listings (update these regularly) |
| `Q` | Interview questions and keywords |

## Limitations

- Hackathon listings are not live. The page cannot fetch them, so keep `H` current and rely on the search buttons.
- Teammates are sample profiles, not real users.
- Accounts do not sync across devices. Real accounts, live hackathon data or AI interview feedback would need a backend.
- Some video links are YouTube searches rather than fixed videos. Replace them with specific videos in `N` if you prefer.

## Roadmap ideas

- Backend sign-in with cloud sync
- Real AI interview feedback
- Scheduled hackathon data
- Export portfolio as a standalone page
- Light and dark theme switch

## License

MIT, see [LICENSE](LICENSE).
