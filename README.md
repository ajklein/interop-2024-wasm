# Interop 2024 WebAssembly Testing Investigation

## Scope

The goal is to get WebAssembly core spec tests running on [wpt.fyi](https://wpt.fyi/) (alongside the existing [JS API](https://wpt.fyi/results/wasm/jsapi?label=experimental&label=master&aligned) and [Web API](https://wpt.fyi/results/wasm/webapi?label=experimental&label=master&aligned) tests). This would open the door for Wasm features to be part of Interop 2025+, and provide greater visibility into the state of Wasm support across browser engines.

Ideally this should require no changes to current practices in the Wasm CG. There already exists an upstream script for running the Wasm spec tests in the WPT harness, which makes it easier to achieve this goal.

## Roadmap

1. Design and build a system to run the Wasm core tests alongside the rest of WPT ([some initial ideas](https://github.com/web-platform-tests/interop/issues/545#issuecomment-1750799558))
2. Get that system approved and running on [wpt.fyi](https://wpt.fyi/)
3. Extend the above to work for in-progress proposals (which are maintained as forks of the main spec repo)

## Scoring

Each item in the roadmap is worth 1/3 of the overall score.

## Original Proposal (from https://github.com/web-platform-tests/interop/issues/545)

### Description

As part of the standardization of new WebAssembly features in the W3C's WebAssembly Community Group, spec tests are required as part of the [feature advancement process](https://github.com/WebAssembly/meetings/blob/main/process/phases.md#4-standardize-the-feature-working-group). And passing those tests is required before a feature becomes fully standardized. But WebAssembly spec tests do not come with a testrunner designed to work in a browser. This is essential to their nature, since they're also meant to be able to be run by non-browser implementations, including the reference interpreter.

This proposal is to investigate adding additional test infrastructure to WPT and wpt.fyi to facilitate running WebAssembly spec tests within the WPT framework.

### Rationale

The major motivation for taking on this work is to enable WebAssembly features to be submitted as Interop proposals without any additional per-proposal overhead (such as manually duplicating tests from the spec repo into WPT).

A secondary motivation is to improve the transparency of WebAssembly feature interop. The state of the art right now is the [Roadmap](https://webassembly.org/roadmap/) page on webassembly.org, which is manually curated. Running Wasm spec tests under WPT would make this data available and automatically up-to-date on wpt.fyi.
