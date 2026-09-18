# Cube Slicer

An interactive version of the classic cube-cutting puzzle:

> Start with a 3×3×3 cube. Cut it into 27 separate 1×1×1 pieces using straight plane
> cuts. You may rearrange the pieces between cuts. What is the fewest number of cuts?

Answer: **6** — and the app shows *why* 6 is unavoidable.

**Play it:** https://axillv.github.io/cube-slicer/

## How it works

- **Slice** — hover a face to preview a plane cut. Cyan means it will divide at least
  one piece; grey means it would pass through a gap. Click to cut. One plane through
  many pieces still costs only one cut.
- **Move** — drag a whole piece to restack it. The nudge pad (`X± Y± Z±`) or the arrow
  keys / `Q` / `E` move the selected piece one unit at a time.
- **Why is 6 the minimum?** — opens the proof: the centre piece is fully enclosed, so
  each of its six faces has to be freed by a cut. The six faces lie in six different
  planes and one flat cut can contain at most one of them, so no clever restacking can
  do better than 6. Two cuts in each of the three directions achieve it.
- Best score is stored in `localStorage`.

## Why the puzzle is interesting

The lower bound is the memorable part: it is a counting argument on the faces of the
one piece you cannot reach. The same "count the things that each move can address"
idea is the key to the tiling problem in the video that popularised this teaser.

## Credits & further reading

- Puzzle popularised by [3Blue1Brown](https://www.youtube.com/watch?v=Nbwv5wHQoj0&t=249s)
  (the 3×3×3 teaser appears around 4:09).
- Also published as [Cubist Cuts](https://nrich.maths.org/problems/cubist-cuts) by NRICH
  (University of Cambridge), which generalises it to n×n×n.
- Everything here (code, layout, text) was written for this project.

## Development

No build step. It is a single static page:

```
index.html            the app
vendor/three.min.js   Three.js r128 (MIT), vendored so the page needs no CDN
vendor/OrbitControls.js
vendor/count.js       GoatCounter beacon (ISC); analytics is cookie-less
```

Open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8000
```

### Analytics

The page reports one pageview plus anonymous events (`engaged-30s`, `engaged-2min`,
`solved-Ncuts`) to a GoatCounter site. No cookies, no personal data; see
https://github.com/axillv/axillv.github.io/blob/main/rclone/privacy.html.

## License

MIT — see [LICENSE](LICENSE). Vendored libraries keep their own licenses
(Three.js and OrbitControls are MIT; GoatCounter's `count.js` is ISC).
