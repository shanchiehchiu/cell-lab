# 🧫 Cell Lab

[繁體中文](README.zh-TW.md) ｜ **English**

Eight interactive simulations where every individual only looks at its neighbors. Each has just a few lines of rules, yet segregation, epidemics, wealth inequality, zebra stripes and order within chaos grow on their own.

One HTML file, zero dependencies, no build step. Open `index.html` and play, or leave it running as a screensaver. The interface is available in **English and Traditional Chinese** (auto-detected, switchable in the panel).

**▶ [Play online: shanchiehchiu.github.io/cell-lab](https://shanchiehchiu.github.io/cell-lab/)**

![Cell Lab demo: reaction–diffusion, Langton's ant, prisoner's dilemma, forest fire, Schelling segregation](docs/demo.gif)

## The eight models

| Model | In one sentence | What you can tune |
|---|---|---|
| **Game of Life** | Two birth/death rules grow gliders, blinkers and glider guns; includes a pattern-recognition radar and collision experiments | Density, speed, chat bubbles |
| **Schelling Segregation** | Nobody wants segregation, only "at least 35% of my neighbors look like me" — yet the city splits into patches | Tolerance, empty lots |
| **Epidemic (SIR)** | Agents move, meet, get infected and recover, with a live infection curve | Infection rate, recovery time, mobility (lockdown), vaccination |
| **Prisoner's Dilemma (spatial)** | Cooperators and defectors copy their best-scoring neighbor; one defector in the center explodes into a kaleidoscope | Temptation b, initial cooperators |
| **Sugarscape** | Two sugar mountains and agents with random vision and metabolism; wealth inequality (Gini coefficient) emerges by itself | Agents, sugar regrowth, vision |
| **Reaction–Diffusion** | The Gray–Scott model grows coral, mazes and dividing-cell patterns | Feed rate f, kill rate k |
| **Forest Fire** | Trees grow, lightning strikes, fire spreads through the forest; fire sizes follow a power law | Growth, spread, lightning rate |
| **Langton's Ant** | An ant with two rules wanders chaotically for ~10,000 steps, then suddenly builds a diagonal "highway" | Rule (RL, RLR…), number of ants |

| | |
|---|---|
| ![Forest Fire](docs/forest.png) | ![Langton's Ant](docs/ant.png) |
| ![Prisoner's Dilemma](docs/pd.png) | ![Sugarscape](docs/sugar.png) |
| ![Schelling Segregation](docs/schelling.png) | ![Reaction–Diffusion](docs/rd.png) |

## How to play

On first load an intro card appears. **Autoplay** is screensaver mode: every 30 seconds it switches to another model with fresh random parameters (tap or move the mouse to stop). **Play myself** gives you the control panel at the top right for switching models and dragging sliders.

| Desktop shortcut | Action |
|---|---|
| Space | Pause / resume |
| `R` | Restart the current model |
| `↑` `↓` | Change speed |
| `U` | Hide / show the UI (`Esc` brings it back) |
| `A` | Toggle auto-rotate |
| Left / right click | Model-specific: draw cells, start a fire, add sugar, drop seeds… (right-click is usually the opposite action) |

On phones the panel sits at the bottom, collapsed by default. When you need a right-click action, tick **Right-click action** in the panel.

### URL parameters

Handy for sharing a specific view:

```
index.html?m=rd&clean=1&steps=450&intro=0&lang=en
```

| Parameter | Description |
|---|---|
| `m` | Model: `life` `schelling` `sir` `pd` `sugar` `rd` `forest` `ant` |
| `clean=1` | Hide the UI |
| `steps=N` | Fast-forward N steps before showing |
| `intro=0` | Skip the intro card |
| `lang` | Interface language: `en` or `zh`. Defaults to your browser language; can also be switched in the panel |

## Deploy to GitHub Pages

1. Create a GitHub repository and push this folder (`index.html` must be at the root).
2. In **Settings → Pages**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. After a minute or two the site is live at `https://<user>.github.io/<repo>/`.
4. In `index.html`, change `og:image` and `og:url` to your full URLs so social platforms can show a preview card.

For local use no server is needed; just open `index.html` in a browser.

## Technical notes

- Plain HTML + Canvas 2D + vanilla JavaScript. No frameworks, no packages.
- All eight models share one grid canvas and one precomputed toroidal neighbor table. A model only defines `reset`, `step`, its colors, and optionally `paint`, `draw` and `overlay`.
- Adding a model means adding one entry to the `MODELS` object; the panel sliders, description, auto-rotation and language switch pick it up automatically.
- Translations live in one `EN` table (Chinese strings are the keys). Sentences with variables use the `L(zh, en)` helper. Static page text is translated by walking the DOM and always translating from the remembered original, so switching back and forth never drifts.

## Further reading

- John Conway, Game of Life (1970)
- Thomas Schelling, *Dynamic Models of Segregation* (1971)
- Kermack & McKendrick, the SIR epidemic model (1927)
- Nowak & May, *Evolutionary games and spatial chaos* (1992)
- Epstein & Axtell, *Growing Artificial Societies* (Sugarscape, 1996)
- Gray & Scott reaction–diffusion; Karl Sims, *Reaction-Diffusion Tutorial*
- Drossel & Schwabl, the forest-fire model (1992)
- Christopher Langton, Langton's ant (1986)

These are simplified teaching models. They illustrate mechanisms; they cannot predict real societies.

## License

[MIT](LICENSE)
