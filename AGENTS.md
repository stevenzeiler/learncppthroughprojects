# AGENTS.md

## Stack
- C++17, CMake 3.17+, Ninja.
- Conan 1.x (the recipe imports `conans`) with boost/1.82.0, openssl/1.1.1w, libcurl/7.88.1, nlohmann_json/3.9.1.
- Tests use Boost.Test.

## Layout
- `inc/network-monitor/`: headers. `src/`: library and `main.cpp`. `tests/`: Boost.Test sources, `cacert.pem`, `network-layout.json`.
- Root: `CMakeLists.txt`, `conanfile.py`, `build.sh`, `Find*.cmake` modules, Conan output files (`conan.lock`, `conaninfo.txt`, `conanbuildinfo.txt`, `graph_info.json`), `table.html` (a saved Conan Center page for boost 1.74.0).
- `docs/STATUS.md`: current state.

## Commands
- Build: see `build.sh` (cmake + ninja inside `build/`) after `conan install`. Never run during the docs pass.
- Tests: `ctest` or `build/network-monitor-tests` (no "test" script). They need network access to `ltnm.learncppthroughprojects.com`.
- Known or likely not to work on today's toolchain: Conan 1.x recipe, OpenSSL 1.1.1w, and the remote server being offline **(inference)**.

## Rules
- Tests with every change.
- Never commit secrets.
- Conventional Commits.
- Keep `docs/STATUS.md` current.
- Keep credit to the course in the README.

## What agents may and may not do
- May: fix build issues, improve docs, add tests, open PRs.
- May not, without Steven: archive, publish, add a licence, rewrite history, or change the upstream-derived exercise design.
