# Rates of Processes, Interactively

An interactive, single-page web demo of nonequilibrium transport: how fast systems approach equilibrium through heat conduction, viscosity, and diffusion, each a flux driven by a gradient.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 1, Section 1.7, an optional section of the course). It follows the demos for Sections 1.1 to 1.3 (temperature and energy) and 1.4 to 1.6 (heat and work).

## What's inside

**Heat conduction.** Conduction at the molecular level, and the Fourier heat conduction law, Q/Δt = −k<sub>t</sub>A dT/dx. A calculator gives the heat flowing through a wall of air, styrofoam, wood, water, glass, iron, or copper for any thickness and temperature difference, and explains why metal feels colder than wood at the same temperature.

**The heat equation (Problem 1.62).** The derivation of ∂T/∂t = K ∂²T/∂x² with K = k<sub>t</sub>/cρ, and a rod solved numerically in real time, with insulated ends. Start from a pulse (compared with the exact solution T<sub>0</sub> + (A/√t) e<sup>−x²/4Kt</sup>), a hot half, or two hot spots, or click to add heat anywhere; the total heat stays constant as it spreads.

**Conductivity of an ideal gas.** The mean free path ℓ ≈ (1/4πr²)(V/N), about 150 nm in air, roughly 40 times the spacing between molecules, with about 3 × 10<sup>−10</sup> s between collisions. A two-dimensional hard-disk gas follows one tracer molecule's zigzag path and measures its mean free path against the estimate. The derivation of k<sub>t</sub> = ½(C<sub>V</sub>/V)ℓv̄ ∝ √T, independent of pressure, with a calculator and chart for air that predicts 0.029 W/(m K) against the measured 0.026.

**Viscosity.** Laminar flow between plates, shear stress |F<sub>x</sub>|/A = η du<sub>x</sub>/dz for air, water, olive oil, or honey, and why gases grow more viscous with temperature while liquids grow less viscous, with data for air and water.

**Diffusion (Problem 1.69).** Fick's law J<sub>x</sub> = −D dn/dx and Fick's second law ∂n/∂t = D ∂²n/∂x², the same equation as for heat. Four thousand dye particles take independent random steps, and their concentration histogram follows the exact solution. A chart of Δt ≈ Δx²/D shows why diffusion is fast over micrometers and hopelessly slow over centimeters: about 4 months for dye to spread 10 cm in water, which is why ink in a glass mixes by convection instead.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The rod uses an explicit finite-difference scheme with a stable timestep and insulated (zero-flux) ends. It matches the exact Gaussian solution to better than 0.1% of the peak before the heat reaches the ends, and conserves the total heat to about 10<sup>−5</sup>.
- The mean-free-path simulation is a two-dimensional gas of equal hard disks with elastic collisions. Its estimate uses the swept area 4rℓ = A/N; because the other molecules also move, the measured value is shorter by about √2, and shorter still at high density.
- The diffusion simulation uses independent Gaussian random walks with reflecting walls, compared with the exact cosine-series solution of Fick's second law for the same box.
- The animations pause when scrolled off screen and start paused when the system asks for reduced motion.
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode via `prefers-color-scheme`, and is responsive down to phone widths.

## Caveats

- Thermal conductivities, viscosities, and diffusion coefficients are typical handbook values; real values vary with temperature, composition, and (for honey) a great deal with the sample.
- The kinetic-theory estimates are deliberately crude, as in the lecture: they capture the scaling (k<sub>t</sub> ∝ √T, independent of pressure) and the rough size, not precise values.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Section 1.7 and Problems 1.62 and 1.69).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
