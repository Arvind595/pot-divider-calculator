# Multiturn potentiometer divider calculator

An interactive, single-page calculator for the output of a potentiometer wired
as a voltage divider, and for the rotation needed to reach a given output.

**Live page:** https://YOUR-USERNAME.github.io/pot-divider-calculator/

> ⚠️ **AI-generated content.** This project was built with the help of an AI
> assistant and reviewed by the author. Verify results before relying on them,
> and check part presets against real datasheets. See [AI_NOTICE.md](AI_NOTICE.md).

## Features

- Drag the knob, or type a rotation, turn count or target output voltage;
  the other values update.
- Part presets (Bourns 3590S, 3540S, 3543S; Vishay Spectrol 534, 533; generic
  single-turn) or fully custom values.
- Models mechanical vs electrical travel (dead band), end resistance and the
  linearity tolerance band.
- Single rail, split (±) or independent rail supplies, with the wiper load
  returned to any reference voltage.
- Solves the loaded wiper node exactly; output-to-angle is solved numerically
  through the full model and warns when a target is out of reach.
- Plots of output and error vs ideal across the full travel.
- No build step and no dependencies apart from one Google Fonts stylesheet.
  Works offline with a system font fallback.

## Model

```
Ideal:      V = V_ccw + (θ / mechanical travel) · (V_cw − V_ccw)
Dead band:  d = (mechanical − electrical) / 2
Position:   k = clamp((θ − d) / electrical, 0, 1)
Resistance: R_ccw = R_end + k (R − 2 R_end),  R_cw = R − R_ccw
Output:     V = (V_cw/R_cw + V_ccw/R_ccw + V_ref/R_L) / (1/R_cw + 1/R_ccw + 1/R_L)
```

θ is measured clockwise from the CCW stop.

## Run locally

Open `index.html` in any modern browser. Nothing to install.

## License

[MIT](LICENSE) © 2026 Arvind
