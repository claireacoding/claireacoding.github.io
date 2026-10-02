# Claire Gunshanan · Portfolio (Tailwind CSS version)

The same portfolio as `portfolio-mockup/`, rebuilt with **Tailwind CSS v4**.

## What is Tailwind?

Tailwind is a CSS framework made of tiny, single-purpose classes called utilities.
Instead of writing a `.card { padding: 32px; border-radius: 28px; }` rule in a
stylesheet, you put classes like `p-8 rounded-card` right on the HTML element.
A build tool then scans your HTML and writes a CSS file containing **only** the
classes you actually used.

## Files

| File | What it is |
|---|---|
| `index.html` | The page. All the styling lives here as Tailwind classes. |
| `input.css` | The Tailwind **source**: imports Tailwind, defines our colors/fonts/sizes in `@theme`, and a few reusable classes (`.card`, `.pill`, `.eyebrow`, `.card-link`). |
| `dist/output.css` | The **compiled** CSS the page actually loads. Generated; don't edit by hand. |
| `package.json` | Lists Tailwind as a tool and defines the `build` / `watch` commands. |
| `.gitignore` | Keeps the big `node_modules/` folder out of git. |

## How to build

You need [Node.js](https://nodejs.org) installed once. Then, in this folder:

```bash
npm install        # first time only: downloads Tailwind into node_modules/
npm run build      # compiles input.css + your classes → dist/output.css (minified)
npm run watch      # while editing: rebuilds automatically every time you save
```

Open `index.html` in a browser to see the result.

> **If a new class does nothing**, the CSS probably wasn't rebuilt. Run
> `npm run build` (or keep `npm run watch` running) and refresh.

## Publishing on GitHub Pages

GitHub Pages only serves files; it does **not** run `npm run build`.
So always **run the build and commit `dist/output.css`** along with your HTML
changes. (`node_modules/` stays out of git; it's only needed on your computer.)

## Mini cheat sheet (classes used on this page)

| Class | Plain English |
|---|---|
| `bg-olive` / `text-olive-dark` | Background / text color from our theme (defined in `@theme`). |
| `p-8`, `px-7 py-3.5` | Padding. Each step is 4px: `p-8` = 32px all around; `px` = left+right, `py` = top+bottom. |
| `rounded-full` | Fully rounded corners (pills and circles). |
| `flex`, `items-center`, `gap-3` | Lay children in a row, centered vertically, 12px apart. |
| `grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4` | A grid with 1 column on phones, 2 from 640px wide, 4 from 960px wide. |
| `sm:col-span-2`, `lg:row-span-2` | Make an item span 2 columns / 2 rows of the grid at that screen size. |
| `hover:bg-olive-dark` | Apply this style only while the mouse is over the element. |
| `focus-visible:outline-3` | Show a 3px outline when someone reaches the element with the keyboard. |
| `motion-safe:hover:-translate-y-1` | Lift the card 4px on hover, but only if the visitor hasn't asked their device for reduced motion. |
| `text-olive/35`, `border-ink/8` | The `/35` means 35% opacity for that color. |
| `text-[0.72em]`, `max-w-[480px]` | Square brackets = a one-off custom value when no preset fits. |
| `group` + `group-open:bg-olive-dark` | Style a child based on its parent's state (here: when the `<details>` is open). |

## Icons

Icons are [Lucide](https://lucide.dev) SVGs pasted directly into the HTML (no icon
library to load). They use `stroke="currentColor"`, so their color follows the
text color: `class="size-4 text-olive-dark"` makes a 16px olive icon.
(The LinkedIn and GitHub icons come from an older Lucide release, since newer
versions dropped brand logos.)
