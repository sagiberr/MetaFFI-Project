# MetaFFI Node.js Runtime Plugin (xllr.nodejs)

## Overview

This project extends the **MetaFFI** framework with full **Node.js runtime support** by implementing a dedicated runtime plugin (`xllr.nodejs`).  

The plugin enables **typed and bidirectional cross-language integration** between Node.js and other MetaFFI-supported languages, including **C++, Python, Java, and Go**.

The goal is to allow Node.js functions and objects to participate naturally in multi-language systems through MetaFFI, without requiring manual per-language-pair bindings.

---

## Architecture

The runtime plugin is composed of the following core components:

- **V8 Embedding Layer (C++)** – Embeds the Node.js (V8) engine within a C++ runtime.
- **Translation Layer (V8 ↔ CDT/CDTS)** – Converts between V8 values and MetaFFI Common Data Types.
- **xcall Invocation Mechanism** – Enables dynamic and typed cross-language function invocation.
- **Runtime Lifecycle Management** – Handles initialization and cleanup of the Node.js runtime.
- **Error & Exception Bridge** – Captures and propagates Node.js exceptions through MetaFFI’s error interface.

This modular architecture ensures type safety, extensibility, and clean separation between runtime control and data translation.

---

## Key Capabilities

- Runtime lifecycle management (initialize/free Node.js runtime)
- Loading Node.js modules and functions as MetaFFI entities
- Typed invocation with parameter and return value handling
- Consistent cross-language type translation (primitives, arrays, handles/objects)
- Exception capture and propagation
- Cross-runtime validation with Python, Java, and Go

---

## Performance Notes

Performance measurements indicate measurable overhead due to abstraction:

- **Direct V8 invocation:** ~0.5 µs per call  
- **MetaFFI-mediated invocation:** ~25 µs per call  

The overhead reflects runtime abstraction and type translation, while preserving cross-language flexibility and safety.

---

## Build Environment

Primary validation environment: **Linux (Docker-based)**

### Dependencies

- `nodejs`
- `npm`
- `libnode-dev`
- `g++` with C++20 support
- `cmake`

Install dependencies (Ubuntu/Debian):

```bash
apt update
apt install nodejs npm libnode-dev cmake g++
