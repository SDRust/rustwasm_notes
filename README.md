# RustWASM Notes #
Notes on a presentation on RustWASM to the San Diego Rust Meetup, September
13th, 2018

## Files in this repo ##
- `README.md` - this file
- `rustwasm_setup.md` - Detailed setup instructions for the RustWASM
  "Game of Life" tutorial
- `rustwasm_workflow.md` - Terse setup instructions, and workflow for the
  RustWASM in general, as well as the "Game of Life" tutorial

## Possible Group Projects ##
Beginner Rust/JavaScript knowledge
- When the page loads, show the grid, but don't automatically start
  calculating generations
- Output universe calculation stats to _JavaScript_ `console.log`
  - Total calcuation time
  - Number of cells that changed state

Intermediate/advanced Rust/JavaScript knowledge
- Calculate sha256 sum in Rust from a string passed in from JavaScript
- Initialize the universe with a single space ship.
- Generate a random grid of cells (50% chance of alive or dead), instead of
  generating the same grid every time programatically
  - The grid generation is done in `lib.rs` (_Universe_ impl)
  - Bonus: allow the size of the universe to be changed prior to populating
    the random universe
- Allow for setting a `range` argument, to control how many ticks are run for
  each animation frame
- Insert a **glider** when the user Ctrl + Clicks on the grid
- Insert a **pulsar** when the user Shift + Clicks on the grid
- Detect when the grid is stable between generations, then pause the
  simulation at that point

Further optimizations that could be done to the tutorial
- Only pass the generation delta (cells that changed) back to the JavaScript
- Use bits to indicate alive/dead cells, instead of bytes
- Double buffering of cells in the _Universe_, so that you don't have to call
  `self.cells.clone()` every time you compute a new generation
- _WebGL_ renderer instead of `<canvas>`
- Shrinking the size of the _WASM_ binary

vim: filetype=markdown tabstop=2 shiftwidth=2
