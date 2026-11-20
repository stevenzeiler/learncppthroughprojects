# learncppthroughprojects

Follow-along code for a C++ course on network programming: a `network-monitor` library and program built with Boost.Asio, TLS, WebSocket, STOMP and libcurl.

**Status:** dormant since 2025-08. 13 commits between 2025-07-16 and 2025-08-01, then nothing. Exercises, not a product.

## Where it comes from

The repo is named after the "Learn C++ through projects" course and talks to that course's practice server (`ltnm.learncppthroughprojects.com`). The exercise design belongs to the course authors, and Steven wrote this code while following along. No upstream repository or licence is recorded in the files **(inference)**.

## What is in it

- `inc/network-monitor/` and `src/`: `WebSocketClient` (Boost.Beast over TLS), `FileDownloader` (libcurl, parses a JSON network layout with nlohmann_json), and a `main.cpp` that connects to the echo endpoint, sends a message and checks the reply.
- `tests/`: Boost.Test tests for both classes, plus `cacert.pem` and a sample `network-layout.json`.
- `CMakeLists.txt`, `conanfile.py`, `build.sh`: build setup (CMake 3.17+, C++17, Conan 1.x).

## Build

From `conanfile.py` and `build.sh` (not run during the docs pass):

```bash
mkdir -p build && cd build
conan install .. --build=missing   # Conan 1.x, requires boost 1.82, openssl 1.1.1w, libcurl, nlohmann_json
cmake .. -GNinja -DCMAKE_BUILD_TYPE=Release
ninja
```

Targets: `network-monitor` (static library), `network-monitor-main`, `network-monitor-tests`. Tests need network access to the course server.

## Config

No environment variables. The server host, endpoint and port are constants in `src/main.cpp`.

## Status and known problems

See [docs/STATUS.md](docs/STATUS.md). The Conan setup uses the old `conans` import (Conan 1.x), and the course server may no longer be running.
