# Zikai's Chess Engine

A chess engine and playable board, entirely in one static `index.html` — no build step, no framework, no server-side code. Move generation (including castling, en passant, and promotion), checkmate/stalemate/draw detection, and an alpha-beta search with iterative deepening and quiescence search are all hand-written in vanilla JavaScript.

## Run it locally

Just open `index.html` in a browser, or serve it:

```bash
npx serve .
```

## Deploy to Vercel

**Option A — Vercel CLI (fastest):**

```bash
npm i -g vercel   # if you don't already have it
cd zikais-chess-engine
vercel            # first deploy: follow the prompts, accept the defaults
vercel --prod     # promote to your production URL
```

No build command or output directory is needed — Vercel serves the static files as-is.

**Option B — GitHub + Vercel dashboard:**

1. Push this folder to a new GitHub repo:
   ```bash
   git init
   git add .
   git commit -m "Zikai's Chess Engine"
   git branch -M main
   git remote add origin <your-repo-url>
   git push -u origin main
   ```
2. Go to [vercel.com/new](https://vercel.com/new), import the repo, and click **Deploy**. Vercel auto-detects it as a static site — leave the build settings blank.

## Project structure

```
index.html      the entire app: markup, styles, and the engine
vercel.json     tells Vercel to serve this as a plain static site
package.json    project metadata (no dependencies)
```

## Customizing

- **Difficulty**: edit `DIFFICULTY_MS` near the top of the second `<script>` block to change how long the engine thinks per level.
- **Colors/fonts**: the full palette lives in the `:root` CSS custom properties at the top of the `<style>` block, with dark-mode overrides just below it.
- **Evaluation**: the piece-square tables and material values are in the first `<script>` block (`PST`, `PIECE_VALUES`) if you want to tune how the engine plays.
