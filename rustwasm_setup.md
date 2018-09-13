- Setup for the Rust WASM "Game of Life" demo
  - `cargo install wasm-pack`
  - `cargo install cargo-generate`
  - `npm` should already be installed
- Cloning the "Game of Life" demo
  - `cargo generate --git https://github.com/rustwasm/wasm-pack-template`
    - You'll be prompted for the target output directory name
      - `wasm-game-of-life`; this will be called `$WASM_GOL` below
- Set up the _wasm-bindgen_ workflow
  - `cd $WASM_GOL`
  - `wasm-pack init`
    - This creates a directory called `${WASM_GOL}/pkg`, with the
      correct _JavaScript_ bits needed to interact with a Rust WASM
      application
    - The _JavaScript_ bits will need to be regenerated via `wasm-pack init`
      every time you make changes to the _Rust_ code
- Create the web app from a template
  - `cd $WASM_GOL`
  - `npm init wasm-app www`
- Install dependencies
  - `cd ${WASM_GOL}/www`
  - `npm install`
- Create local (non-NPM links)
  - `cd ${WASM_GOL}/pkg`
  - `npm link`
- Create links to the local non-NPM packages
  - `cd ${WASM_GOL}/www`
  - `npm link wasm-game-of-life`
- Edit `${WASM_GOL}/www/index.js`, and change the name of the package to use
  - `cd ${WASM_GOL}/www`
  - `vim index.js`
  - Do `s/hello-wasm-pack/wasm-game-of-life/` in the line
    `import * as wasm from "hello-wasm-pack"`
- Start a dev web server in the application directory
  - `cd ${WASM_GOL}/www`
  - `npm run start`
    - The dev web server will pick an unused port on the local machine and
      start serving web pages via HTTP
    - Look for the server URI in the log output when starting the dev web
      server
      - "Project is running at http://localhost:8081/"
- Make changes to the source as needed, then rerun the `wasm-pack` command
  again
  - `cd $WASM_GOL`
  - `wasm-pack init`