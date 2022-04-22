# pysvelte

_**Main idea:** Create a static site that supports collaborative python programming (i.e. [replit](https://replit.com/) without the server)._

---

Implementation path w/ progress:

- [x] Svelte project
- [x] Run wasm from rust Package
- [x] Run wasm within web worker
- [ ] Run python code using RustPython compiled to wasm.
- [ ] Add nice editor (monaco, codemirror, etc.)
- [ ] Add CRDT/collaboration with [yjs](https://docs.yjs.dev/)
- [ ] Add webrtc hookups for yjs/collaboration on _editor code_
- [ ] Add CRDT validation of python editor output/state.

# Features

Glues a lot of components together, particularly in the sveltekit/vite context:

- [x] WASM
  - [x] Simple/example wasm (i.e. greet, fibonacci)
  - [ ] Non-trivial WASM (i.e. make use of a complex crate)
- [x] Web workers (w/ typescript)
- [ ] Rich editors
- [ ] WebRTC
- [ ] YJS

# Development

_In development, web workers will only work well/hot reload in chromium-based browsers!_ (Or, at least, firefox does not work.)

## Build wasm

```bash
cd src/lib/wasm
wasm-pack build --target web --dev

# To build
wasm-pack build --target web

# https://github.com/rustwasm/wasm-pack/issues/457#issuecomment-457024036
# cargo install cargo-watch
cargo watch -i .gitignore -i "pkg/*" -s "wasm-pack build --target web --dev"
```

## RustPython work

❗ IMPORTANT: Before going any further, run this command:

```bash
rustup update stable
```

# Acknowledgements

- [Svelte/Svelte kit](kit.svelte.dev)
- [RustPython](https://github.com/RustPython/RustPython)
- [rustwasm/wasm-pack](https://github.com/rustwasm/wasm-pack)
- [vite](https://vitejs.dev/)
