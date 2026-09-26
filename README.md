# Valorant Weapon Roulette

An interactive spinning wheel that decides which weapon you play in Valorant.
One HTML file, no dependencies, no install — just open it in a browser.

**[Live demo](https://EnriqueFelixR.github.io/valorant-weapon-roulette/)**

## Usage

Open `index.html` in any browser and click a wheel to spin it. The winning
weapon appears below the wheel and its slice is highlighted. The **Spin all**
button spins every wheel at once.

## Included wheels

**By weapon class**

| Class | Weapons |
|---|---|
| Sidearms (Pistols) | Classic, Shorty, Frenzy, Ghost, Sheriff, Bandit |
| SMGs | Stinger, Spectre |
| Shotguns | Bucky, Judge |
| Rifles | Bulldog, Guardian, Phantom, Vandal, Warden |
| Snipers | Marshal, Outlaw, Operator |
| Heavies (LMGs) | Ares, Odin |

Plus one large wheel holding all 20 weapons together.

**By credits** (based on the round's economy)

| Wheel | Weapons |
|---|---|
| Pistols — pistol round | Classic, Shorty, Frenzy, Ghost, Sheriff, Bandit |
| Mid — round lost | Stinger, Marshal, Bucky, Sheriff |
| Mid — round won | Spectre, Ares, Outlaw, Bulldog, Guardian, Judge |
| High — full buy | Odin 20%, Vandal 30%, Phantom 30%, Warden 20% |

## Configurable odds

By default every weapon on a wheel is equally likely. To weight them, add a
`weights` array to the matching entry in `CLASSES` or `CREDITS` inside the
`<script>`:

```js
{ name: "High", weapons: ["Odin","Vandal","Phantom","Warden"], weights: [20, 30, 30, 20] }
```

The numbers are relative — they don't have to add up to 100 — and each slice is
drawn proportional to its weight, so the wheel itself shows how likely every
weapon is.

## Implementation notes

- Plain HTML, CSS and JavaScript, rendered on a `<canvas>`.
- Spin animated with `requestAnimationFrame` and quartic easing (4–5.5 s, 5–8 turns).
- The winner is drawn first via cumulative-weight selection, then the target
  angle is computed from it — so the wheel always stops on the weapon it picked.
- No libraries, no build step, no server.

## License

MIT — see [LICENSE](LICENSE).

## Disclaimer

A fan project, not affiliated with or endorsed by Riot Games. Valorant is a
trademark of Riot Games, Inc.
