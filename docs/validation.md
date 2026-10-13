# wondertrader: validation results

<!-- current-documentation-provenance -->
Documentation reviewed: 2026-10-13 / Git source base: `a9470813cedef7373bfe7e72ffeadf13d6484a75` / [Current architecture and feature guide](ayu-develop.md).
Historical execution commands/results below retain their original dates and scope; this metadata update is not a new application test run.
<!-- /current-documentation-provenance -->


All native targets built and the complete supplied unit binary passed on Linux/amd64.

## Verified scope

16 of16 supplied TestUnits cases passed on Linux-local storage.

The macOS build attempt cannot link the bundled Linux vendor SDKs. Real LMDB error propagation, octal directory permissions, GCC8 filesystem linkage, local shared-memory fixture paths and midnight session normalization were repaired. No test cases were added; existing assertions were retained.

## Environment

Official repository Docker Linux/amd64 build image and bundled mydeps_gcc8.4.0 archive

## Executed checks

Exploratory failures remain visible. Use later successful runs only for the scope they actually exercised; builds, syntax checks and benchmark smoke runs are distinct from complete test suites.

| Check | Exit | Duration | Command |
| --- | ---: | ---: | --- |
| cmake-configure | 0 | 3.33s | `cmake -S src -B build/ayu -DCMAKE_POLICY_VERSION_MINIMUM=3.5 -DCMAKE_BUILD_TYPE=Release` |
| docker-build | 1 | 30.05s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z && cd /workspace && cmake -S src -B build/ayu-linux -DCMAKE_BUILD_TYPE=Release && cmake --build build/ayu-linux --parallel 4` |
| linux-build | 2 | 419.74s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z && mkdir -p /workspace/build/ayu-linux && cd /workspace/build/ayu-linux && cmake ../../src -DCMAKE_BUILD_TYPE=Release && make -j4` |
| linux-build-filesystem | 0 | 163.97s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z && cd /workspace/build/ayu-linux && cmake ../../src -DCMAKE_BUILD_TYPE=Release && make -j4` |
| linux-existing-tests | 139 | 3.15s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace/build/ayu-linux/build_x64/Release/bin/TestUnits wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z >/dev/null && cd /workspace/build/ayu-linux/build_x64/Release/bin/TestUnits && LD_LIBRARY_PATH=.:/home/mydeps/lib/linux/gcc/x64 ./TestUnits </dev/null` |
| linux-final-full-build | 0 | 161.4s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z >/dev/null && cd /workspace/build/ayu-linux && make -j4` |
| linux-lmdb-build-and-test | 1 | 12.96s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z >/dev/null && cd /workspace/build/ayu-linux && make -j4 TestUnits && cp -a build_x64/Release/bin/TestUnits /tmp/wt-tests && cd /tmp/wt-tests && rm -rf testdb endiandb && LD_LIBRARY_PATH=.:/home/mydeps/lib/linux/gcc/x64 ./TestUnits </dev/null` |
| linux-local-filesystem-tests | 1 | 4.08s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z >/dev/null && cp -a /workspace/build/ayu-linux/build_x64/Release/bin/TestUnits /tmp/wt-tests && cd /tmp/wt-tests && rm -rf testdb endiandb && LD_LIBRARY_PATH=.:/home/mydeps/lib/linux/gcc/x64 ./TestUnits </dev/null` |
| linux-session-shared-fixtures-tests | 0 | 40.69s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z >/dev/null && cd /workspace/build/ayu-linux && make -j4 TestUnits && cp -a build_x64/Release/bin/TestUnits /tmp/wt-tests && cd /tmp/wt-tests && rm -rf testdb endiandb && LD_LIBRARY_PATH=.:/home/mydeps/lib/linux/gcc/x64 ./TestUnits </dev/null` |
| linux-tests-fixtures | 139 | 3.18s | `docker run --rm --platform linux/amd64 --volume /Users/alex/workspaces/trading/wondertrader:/workspace --workdir /workspace/build/ayu-linux/build_x64/Release/bin/TestUnits wondertrader/wondertrader:latest bash -lc cd /home && 7za x -y /workspace/docker/mydeps_gcc8.4.0.7z >/dev/null && cd /workspace/build/ayu-linux/build_x64/Release/bin/TestUnits && mkdir -p testdb endiandb && LD_LIBRARY_PATH=.:/home/mydeps/lib/linux/gcc/x64 ./TestUnits </dev/null` |
| native-build | 2 | 11.51s | `cmake --build build/ayu --parallel 4` |

## Portable evidence

[Executed command records](maintenance/index.html) · [Machine-readable verification](maintenance/verification.json) · [Engineering guide](ayu-develop.md) · [Development workflow](development.md)

Full original logs are retained in the workspace maintenance evidence; portable records contain their hashes, exact execution metadata and available outcome lines.
