# Dorestep

**Where Vanderbilt disciplines meet.** Dorestep connects students who are researching, building, or founding something with students looking to get involved, especially across schools. The collaborator your project is missing is probably not in your major.

Brought to you by the College of Connected Computing at Vanderbilt University.

> **This is a demo.** All students, projects, and activity in it are fictional. The schools, programs, and the Wond'ry / Immersion Vanderbilt references are real. It is a single self-contained front-end prototype: there is no backend, no real accounts, and no real data leaves your browser. It exists to show what the product could be, not to operate as a live service.

## What it does

- **Discover feed** with explained, ranked matches (skill complementarity, shared interests, cross-school bonuses, a semantic concept layer, mentor fit, and schedule overlap), plus thumbs up/down that tunes future suggestions.
- **People, Projects, Calls, and Mentors** directories with search and filters.
- **Cold-start in under a minute:** paste a resume or bio to auto-fill skills and interests, and join existing communities (a course, the Wond'ry, AnchorLink orgs) to seed your network.
- **Profiles** with illustrated avatars, interest and skill tags, weekly office-hours availability, and peer vouches tied to completed work.
- **Connections and a simulated inbox** with typing indicators, read receipts, a smart scheduler, and Google Calendar / .ics export.
- **Outcomes:** project status tracking, a completed-collaborations showcase, and downloadable resume-ready portfolio entries.
- **Safety affordances:** report, block, and cold-outreach rate limits.

Everything you do persists in your browser via `localStorage`. The footer has a "Reset demo" link that clears it.

## Run locally

Either open `index.html` directly in a browser, or serve it (recommended, so hash routing and fonts behave exactly as in production):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

This folder is already a git repository with an initial commit. To publish:

1. Create a new **public** repository on GitHub, for example `dorestep` (do not add a README, license, or .gitignore from the GitHub side, this folder already has them).
2. From inside this folder, point it at your new repo and push:
   ```bash
   git remote add origin https://github.com/YOUR-USERNAME/dorestep.git
   git push -u origin main
   ```
3. On GitHub, go to **Settings > Pages**. Under **Build and deployment**, set **Source** to "Deploy from a branch," choose branch **main** and folder **/ (root)**, then **Save**.
4. Wait about a minute. Your demo will be live at:
   ```
   https://YOUR-USERNAME.github.io/dorestep/
   ```

The `.nojekyll` file tells GitHub Pages to serve the files as-is without Jekyll processing.

## Demo shortcuts

Append these to the URL to jump into a populated state (useful for showing the demo without clicking through setup):

- `#/discover?seedme` seeds a sample visitor profile (a CCC student building a music tool) so personalized matches appear immediately.
- `#/inbox?seedme&flow` also seeds an accepted connection and conversation, including a proposed meeting.
- `#/discover?onboard=1` opens the onboarding wizard.
- `#/projects?seedme&post=1` opens the "Post a project" flow.

Example: `https://YOUR-USERNAME.github.io/dorestep/#/discover?seedme`

## Beyond the demo

This prototype is the front end. A real, multi-user Dorestep would need a backend that GitHub Pages cannot host on its own (Pages serves static files only). A realistic path:

- **Data and auth:** a service such as Supabase or Firebase, with sign-in restricted to `@vanderbilt.edu` (Vanderbilt runs Google Workspace), and real SSO via VUIT later.
- **Hosting:** keep this static front end on Pages and talk to that backend, or move to a full-stack host (Vercel, Netlify, Render).
- **Before any real student data goes in:** loop in the College of Connected Computing and Vanderbilt IT. Real names, profiles, and messages are student data with privacy obligations, and should not live on a personal account without institutional buy-in.

The seed data in `index.html` doubles as a working schema (students, projects, calls, vouches, connections, messages, communities), and the matching engine is plain JavaScript that can move server-side or stay on the client.

## Tech

One self-contained HTML file: inline CSS and vanilla JavaScript, no build step and no dependencies except Google Fonts loaded from their CDN. Vanderbilt brand typography (Libre Caslon Text, Inter, Antonio) and official brand colors throughout.
