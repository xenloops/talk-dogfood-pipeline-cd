# Build verification


Things to keep in mind:

* Goal: provably verify that code going in matches binary coming out
* Use cryptographically strong functions (e.g. SHA-256 hash)
* Calculate hash values (and store them) separately and securely
* Use best practices to secure the pipeline, its tools, and storage
* Define the build environment specifications explicitly
* Isolate the build environment
* Log all activities in the build pipeline, and audit randomly

<br /><br /><br /><br />

### Overall process

1. In development environment:
   1. Create hash from pushed code and store it
3. In CI part of pipeline:
    1. Pull copy of repo
    2. Hash pulled code when the build runs
    3. Compare hashes -- if same, continue
    4. Build code
    5. Create hash from binary/runtime and store it
    6. Rest of pipeline work
1. In CD part of pipeline:
    1. Get binary, runtime files (if needed)
    2. Hash files
    3. Compare to previous hash -- if same, continue
    4. Deploy binary

<br /><br /><br /><br />


[Next slide](lessons_outcomes.md)
