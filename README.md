# Pixel Paint: Flood Fill Exercise

Welcome! In this exercise you'll finish a small feature in a working pixel-art editor. There's no trick to the setup: everything you need is in one HTML file, and you'll spend your time on the problem itself.

## Getting started

1. Open `pixel-paint-starter.html` in a browser (Chrome, Firefox, Edge or Safari).
2. Open the same file in your editor.
3. After each change, save the file and reload the browser tab.

If a yellow note appears in the tests panel saying background workers are blocked, serve the folder locally instead of opening the file directly:

```
python3 -m http.server
```

Then visit `http://localhost:8000/pixel-paint-starter.html`.

## The app

Pixel Paint is a simple editor with a 256 × 256 canvas and a 16-color palette.

- **Pencil** paints one pixel at a time.
- **Brush** paints with a round tip; set its size with the slider.
- **Fill** is the paint bucket. It doesn't work yet, and that's your task.

Left click paints with the primary color and right click with the secondary. Choose colors from the palette the same way. **Test shapes** draws a few outlines you can use to try your fill, and **Undo** (Ctrl/Cmd + Z) reverts any change.

## Your task

Implement the `floodFill` function at the top of `pixel-paint-starter.html`.

When the user clicks with the Fill tool, the clicked pixel and every pixel connected to it through pixels of the same color should change to the selected color. This is the paint bucket you've used in other drawing programs.

```js
function floodFill(pixels, width, height, startX, startY, fillColor) {
  // TODO: implement me.
}
```

| Parameter | Type | Meaning |
|---|---|---|
| `pixels` | `Uint8Array` | The canvas. Modify it in place. |
| `width` | number | Canvas width in pixels |
| `height` | number | Canvas height in pixels |
| `startX` | number | Column of the clicked pixel |
| `startY` | number | Row of the clicked pixel |
| `fillColor` | number | Palette index to paint with (0–15) |

The function doesn't return anything.

## How the canvas is stored

The canvas is a flat array with one byte per pixel. Each byte is a palette index from 0 to 15, not an RGB value.

Pixels are stored row by row, starting at the top-left corner. `x` increases to the right and `y` increases downward:

```
index = y * width + x
```

For example, on a 4 × 3 canvas the indices are laid out like this:

```
        x=0  x=1  x=2  x=3
  y=0    0    1    2    3
  y=1    4    5    6    7
  y=2    8    9   10   11
```

Two pixels count as connected when they share an edge: up, down, left or right. Pixels that only touch at a corner are not connected.

The app's canvas is 256 × 256, but your function should work for any width and height.

## Checking your work

There are two ways to check your implementation.

- **On the canvas.** Pick the Fill tool, choose a color and click. The status line under the canvas shows how many pixels changed and how long it took. If something goes wrong, the error message appears there too.
- **With the tests.** Press **Run tests** in the right-hand panel. Failing tests show the grid before the fill, what was expected and what your code produced.

Your code runs in the background with a time limit, so if it never finishes, the page stays responsive and reports a timeout.

## Rules

- Write your code inside the `<script id="flood-fill-impl">` block at the top of the file. Put any helper functions in that block too.
- You don't need to change anything else in the file, but you're welcome to read it.
- Use plain JavaScript; no libraries.
- Ask your interviewer if you're unsure what reference material you can use.

## What we're looking for

We're more interested in how you approach the problem than in a perfect first attempt.

- **Think out loud.** Explain your approach before and while you code.
- **Ask questions.** If something about the requirements is unclear, ask, just as you would at work.
- **Iterate.** A simple working version you then improve is a fine way to go.
- **Reason about your solution.** Be ready to discuss how it behaves, how fast it is and how much memory it uses.

Good luck, and have fun!
