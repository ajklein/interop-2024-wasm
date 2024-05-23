# Interop 2024 WebAssembly Testing Investigation

## Original Proposal (from https://github.com/web-platform-tests/interop/issues/545)

### Description

As part of the standardization of new WebAssembly features in the W3C's WebAssembly Community Group, spec tests are required as part of the [feature advancement process](https://github.com/WebAssembly/meetings/blob/main/process/phases.md#4-standardize-the-feature-working-group). And passing those tests is required before a feature becomes fully standardized. But WebAssembly spec tests do not come with a testrunner designed to work in a browser. This is essential to their nature, since they're also meant to be able to be run by non-browser implementations, including the reference interpreter.

This proposal is to investigate adding additional test infrastructure to WPT and wpt.fyi to facilitate running WebAssembly spec tests within the WPT framework.

### Rationale

The major motivation for taking on this work is to enable WebAssembly features to be submitted as Interop proposals without any additional per-proposal overhead (such as manually duplicating tests from the spec repo into WPT).

A secondary motivation is to improve the transparency of WebAssembly feature interop. The state of the art right now is the [Roadmap](https://webassembly.org/roadmap/) page on webassembly.org, which is manually curated. Running Wasm spec tests under WPT would make this data available and automatically up-to-date on wpt.fyi.

### Investigation Roadmap

1. The WPT test runner would need to be updated with glue code to adapt Wasm spec tests to the WPT runner
2. wpt.fyi would need logic to fetch spec tests from https://github.com/WebAssembly/spec/tree/main/test/core (for the currently-standardized spec) or from individual proposals under the WebAssembly Github organization, then run them using the updated runner
