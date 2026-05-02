# Learn — Daily Python Skills

A self-contained section of `pradeepgadde.com` for posting one Python skill per day. Built as plain HTML/CSS so it works on GitHub Pages with no Jekyll dependency, no build step, and no plugins.

## Folder layout

```
learn/
├── index.html              # Landing page with the grid of all entries
├── _template.html          # Copy this when adding a new day
├── README.md               # You are here
├── assets/
│   └── learn.css           # All styles for the section
└── posts/
    └── day-001-f-strings.html
```

## Deploying

This folder is designed to drop directly into the root of your existing GitHub Pages repository. Put it next to your `blog/` folder and it will be served at `pradeepgadde.com/learn/` — no config changes needed.

Files in this folder have no Jekyll front matter, so Jekyll will pass them through to `_site/` unchanged.

If you ever want to be explicit about it, you can add this to `_config.yml`:

```yaml
include:
  - learn
```

## Publishing a new daily post (the 2-minute workflow)

1. **Copy the template:**
   ```bash
   cp learn/_template.html learn/posts/day-002-pathlib.html
   ```

2. **Open the new file** and fill in:
   - `<title>` and `<meta description>`
   - The `day-marker`, `<h1>`, `subtitle`, and date in the article header
   - The TL;DR
   - Body sections — each `<h2>` becomes a section
   - Code blocks — see the syntax token cheat-sheet at the bottom of `_template.html`
   - The "Try it yourself" challenge
   - The prev link (point at the previous day's file)

3. **Update yesterday's post** so its `next` link points to today instead of the placeholder.

4. **Add a card to `learn/index.html`** at the top of the `<div class="posts">` block. Use this snippet:

   ```html
   <a class="post-card" href="posts/day-002-pathlib.html">
     <span class="day-no">Day 002 &middot; Standard library</span>
     <h3>Stop using os.path. Use pathlib.</h3>
     <p class="excerpt">One-sentence teaser that makes them want to click.</p>
     <div class="meta">
       <div class="tags">
         <span class="tag">stdlib</span>
         <span class="tag">files</span>
       </div>
       <span class="arrow" aria-hidden="true">↗</span>
     </div>
   </a>
   ```

   Move the `featured` class from the old top card to the new one if you want the latest entry to be visually emphasized.

5. **Commit and push.** GitHub Pages picks it up in ~30 seconds.

## Code block syntax

Code blocks are just `<pre>` tags with hand-marked tokens — no client-side highlighter, no flash of unstyled code, instant render. Wrap text in these classes inside the `<code>` block:

| Class | Color | For |
|-------|-------|-----|
| `tok-c` | muted italic | comments |
| `tok-s` | warm gold | strings |
| `tok-k` | coral | keywords (`def`, `for`, `if`, `import`, `class`, `return`, `with`, `lambda`) |
| `tok-n` | light blue | numbers and variable names |
| `tok-f` | soft green | function names being called |
| `tok-o` | yellow | an operator you want to call out |

It's hand-coloring, which sounds tedious but takes ~30 seconds for a typical snippet and gives you a much more striking result than auto-highlighting.

If you'd rather use an automatic highlighter later, drop in [Prism.js](https://prismjs.com/) or [Shiki](https://shiki.style/) — both are CDN-friendly.

## Callouts available

```html
<div class="tldr">
  <div class="tldr-label">TL;DR</div>
  <p>One-sentence summary.</p>
</div>

<div class="callout">
  <p>Pro-tip or aside.</p>
</div>

<div class="callout warn">
  <p>Warning or gotcha.</p>
</div>

<div class="challenge">
  <p>Concrete thing to try right now.</p>
</div>
```

Output blocks (faux REPL output below a code block):

```html
<div class="output">whatever your code printed</div>
```

## Design notes

- **Typography:** Fraunces (display), Newsreader (body), JetBrains Mono (code), and Caveat for the handwritten "Pradeep Gadde" brand mark — all from Google Fonts.
- **Palette:** warm parchment (`#f7f1e3`) with deep ink, Python yellow as accent, Python blue for links.
- **Theme:** the aesthetic is a "field journal" / typeset newspaper, not a generic dev blog. Adjust the CSS variables at the top of `learn.css` to retheme the whole section in seconds.
- **No JS frameworks.** A tiny inline script on the index page counts the cards and updates the stat — that's it.

### Swapping the brand handwriting font

The `Pradeep Gadde` topbar mark uses **Caveat**. To change it:

1. In `assets/learn.css`, edit the `@import` URL at the top to reference whatever Google Font you prefer (e.g. `Kalam`, `Patrick+Hand`, `Indie+Flower`, `Sacramento`).
2. Change the `--font-brand` CSS variable in the `:root` block to match. That single variable controls every appearance of the brand text.

## Ideas for future days

A starter list so you don't stall on Day 002:

- pathlib over os.path
- `collections.Counter` for tallying anything
- `dict.get(key, default)` and `dict.setdefault`
- `enumerate` and the underused `start=1` parameter
- The walrus operator `:=`
- `dataclasses` and `kw_only=True`
- f-string `{!r}` vs `{!s}` conversions
- `functools.cache` for memoization in one line
- `itertools.batched` (Python 3.12+)
- `subprocess.run` done right
- `argparse` in 10 lines
- Context managers with `contextlib.contextmanager`
- `pytest`-style assertions vs unittest
- Type hints: `Optional`, `Union`, the `|` shorthand
- `*args`, `**kwargs`, and positional-only parameters (`/`)
- `match` statements beyond the basics
- Generators and `yield from`
- `__slots__` for memory savings
- Virtual environments with `uv`
- `pyproject.toml` instead of `setup.py`
