# Status

Last reviewed: 2026-11-20 (github-audit pass 02, docs only). Nothing was built or run.

## What works
- Per the git log, each course step was committed as it was finished: Asio basics, `WebsocketClient`, static library, TLS handshake, STOMP connect frame, libcurl download and JSON parse.
- Whether it builds today is unknown.

## What's broken or unknown
- Conan 1.x recipe (`from conans import ConanFile`); Conan 2 will not accept it.
- OpenSSL 1.1.1w is end-of-life.
- Tests and `main.cpp` need the course server to be up.
- `CMakeLists.txt` references a `cmake/` folder that is not in the repo.
- Committed generated files: `conan.lock`, `conaninfo.txt`, `conanbuildinfo.txt`, `graph_info.json`, `table.html`.
- `tests/websocket-client.cpp` uses obviously fake credentials (`fake_username`); no real secrets found.

## What's next
- Nothing planned. Steven to decide: leave as a learning record, or archive.

## Not yet from the standard
- LICENSE: none declared. Public repo built from a course, so Steven's decision (check the course terms first).
- CONTRIBUTING, SECURITY, `.editorconfig`, `.github` templates, Dependabot, `ci.yml` with gitleaks.
- CloudEvents catalog, product ONE-PAGER.
- The default branch is already `main`.
