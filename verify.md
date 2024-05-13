# Build verification

## What are some things that can go wrong with the build pipeline?

<details>
  <summary> Think: </summary>

* Spoofing
* Tampering
* Repudiation
* Info disclosure
* Elevation of privilege

</details>

<br /><br /><br /><br />

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

1. Periodically create hash from pulled code and store it securely separately (with signature)
2. In CI part of pipeline:
    1. Pull copy of repo
    2. Hash pulled code when the build runs
    3. Compare hashes -- if same, continue
    4. Build code
    5. Create hash from binary/runtime and store securely separately
    6. Rest of pipeline work
1. In CD part of pipeline:
    1. Get binary, runtime files (if needed)
    2. Hash files
    3. Compare to previous hash -- if same, continue
    4. Deploy binary

<br /><br /><br /><br />

Generating and validating hashes

* Linux built-in: ```shasum```
* Use SHA-256: ```shasum -a 256 [file]```
* Write it to a file: ```shasum -a 256 [file] > [file]```
* Compare a file to its hash: ```shasum -c [file]```
  * If the file and its hash match, returns ```[file]: OK```
  * Otherwise: ```shasum: WARNING: 1 computed checksum did NOT match```




