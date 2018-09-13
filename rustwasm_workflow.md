# Initial Setup #

    # Cloning GOL repo...
    cd $WORK_DIR
    git clone https://github.com/rustwasm/wasm_game_of_life.git

    export WASM_GOL=${WORK_DIR}/wasm_game_of_life
    cd $WASM_GOL

    # set up 'pkg/' directory
    wasm-pack init

    # Install NPM dependencies for web app
    cd ${WASM_GOL}/www
    npm install

    # Create local (non-NPM) links
    cd ${WASM_GOL}/pkg
    npm link

    # Create links to the local non-NPM packages
    cd ${WASM_GOL}/www
    npm link wasm-game-of-life

    # Start a dev web server in the application directory
    cd ${WASM_GOL}/www
    npm run start

- The dev web server will pick an unused port on the local machine and start
  serving web pages via HTTP
- Look for the server URI in the log output when starting the dev web server
  - "Project is running at http://localhost:8081/"

# Development Workflow #
If you make changes to the _Rust_ source, rerun `wasm-pack`


    cd $WASM_GOL
    wasm-pack init

If you make changes to the _JavaScript_ source in `index.js` the NPM
development server will pick up those changes, and automatically reload the
file.
