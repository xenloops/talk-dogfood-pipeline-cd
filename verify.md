# Build verification

Things to keep in mind:

* Goal: provably verify that code going in matches binary coming out
* Use cryptographically strong functions (e.g. SHA-256 hash)
* Calculate hash values (and store them) separately and securely
* Use best practices to secure the pipeline, its tools, and storage
* Define the build environment specifications explicitly
* Isolate the build environment
* 

### Overall process

1. Periodically create hash from pulled code and store it securely separately (with signature)
2. In pipeline:
    1. Pull copy of repo
    2. Hash pulled code when the build runs
    3. Compare hashes -- if same, code hasn't been tampered with
    4. Build code
    5. Create hash from binary
4. Compare 


