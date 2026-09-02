# S Sri Ram — Portfolio

A single-file, dependency-free portfolio site (`index.html`). No build step required — Tailwind, fonts, and icons load from CDN.

## Run it locally

You can just double-click `index.html` to open it in a browser. For a proper local server (recommended, since some browsers restrict `download` links on `file://`):

```bash
# Python (most systems already have this)
cd portfolio
python3 -m http.server 8000
# then open http://localhost:8000

# or, if you have Node:
npx serve .
```

## Deploy it

Drag the `portfolio` folder into [Vercel](https://vercel.com/new) or [Netlify Drop](https://app.netlify.com/drop), or push it to a GitHub repo and enable GitHub Pages. No build command is needed — it's static HTML.

## Add your resume

Put your PDF at:

```
resume/S_Sri_Ram_Resume.pdf
```

The "Download Resume" buttons already point to `/resume/S_Sri_Ram_Resume.pdf`. If you deploy to a subpath (e.g. GitHub Pages project sites), update that path in `index.html` (search for `resume/S_Sri_Ram_Resume.pdf` — it appears 3 times) to match.

## Add your profile photo

Drop an image into `assets/` (e.g. `assets/profile.jpg`) and reference it wherever you'd like — the current hero is text-led with a PCB-trace background and doesn't require one, but you can add an `<img>` next to the hero heading if you want a headshot.

## Update your real email

Search `index.html` for `your.email@example.com` and replace both occurrences (the `mailto:` link and its visible text) with your real address.

## Add a new project

Open `index.html`, find the `const projects = [...]` array near the bottom, and copy one of the existing objects as a template:

```js
{
  title: "Your Project Title",
  date: "Month Year",
  type: "Academic Project", // or "Personal Project", "Hackathon", etc.
  tech: ["Tech 1", "Tech 2"],
  description: "One or two sentence summary.",
  contributions: ["What you did", "What you built"],
  github: "https://github.com/you/repo", // or null if none
}
```
It will render automatically — no HTML/CSS editing needed.

## Add a new internship / experience entry

Same pattern — edit the `const experience = [...]` array. Entries render in the order given, so add new ones wherever they belong chronologically.

## Add skills, certificates, or achievements

- **Skills:** edit the `const skills = [...]` array (add a new category object, or push items into an existing category's `items` array). Icons come from [Lucide](https://lucide.dev/icons) — use any icon name as a string.
- **Certificates / achievements:** these aren't in the current brief (no real ones were provided), so there's no section yet. To add one later, copy the structure of the "Career Focus" grid (`focusAreas` array + `#focusGrid` render block) as a starting pattern — a titled grid of cards is the simplest fit.

## Connect the contact form to a backend

The form in `#contact` is frontend-only right now (see `contactForm` in the `<script>` at the bottom of `index.html`). To make it actually send messages, either:
1. Use a form backend service (Formspree, Getform, Web3Forms) — point the `<form>`'s `action` at their endpoint and remove the `preventDefault()` in the submit handler, or
2. Replace the handler with a `fetch()` call to your own API endpoint.

## Notes on content accuracy

Every fact in this site (education, CGPA, internships, projects, dates, links) was taken directly from what you provided — nothing was invented. Two fields are intentionally left as placeholders because they weren't provided: your email address and the resume PDF file itself.
