# Uses

Rust (`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`)
wasm-pack (`curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh`)
wasm-bindgen-cli (`cargo install wasm-bindgen-cli --force --git https://github.com/rustwasm/wasm-bindgen`)

## BUILD
`WASM_INTERFACE_TYPES=1 wasm-pack build`

`wasm-bindgen target/wasm32-unknown-unknown/release/markdown.wasm --out-dir .`

## NOTES

WebAssembly has 2 priniciples baked into it: portability and security.

Uses WebAssembly Interface types - addresses the need for communication with WebAssembly to extend past "talking" in numbers.
- When JS and WebAssembly try to talk to each other they currently end up using different types.
- Translation was/is needed to turn an array of numbers into a string and then back into numbers (wasm-bindgen and emscripten's Embind - these automatically create the js glue code to do this translation)

WebAssembly is an assembly language for a conceptual machine, not a physical one. This is why it can be run across a variety of different machine architectures.

WebAssembly Reference Types proposal is a way to solve the translation complexity challanges by introducing `anyref`. That way consumers can pass over a pointer to an object and WASM can just pass that along to other JS functions.

### Benefits
Using WebAssemlby "Native" modules we can get the benefits of speed without the complexity of target device compilation.

Provides lightweight sandboxing (Code cannot talk directly to the OS) by default to increase the security of the consuming applications (WASI - WebAssembly System Interface).

### References

WA Reference types proposal: https://github.com/WebAssembly/reference-types/blob/master/proposals/reference-types/Overview.md#language-extensions

WASI: https://hacks.mozilla.org/2019/03/standardizing-wasi-a-webassembly-system-interface/
