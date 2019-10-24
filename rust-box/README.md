# Uses

Rust (`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`)
wasm-pack (`curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh`)
wasm-bindgen-cli (`cargo install wasm-bindgen-cli --force --git https://github.com/rustwasm/wasm-bindgen`)

## BUILD
`WASM_INTERFACE_TYPES=1 wasm-pack build`

`wasm-bindgen target/wasm32-unknown-unknown/release/markdown.wasm --out-dir .`

