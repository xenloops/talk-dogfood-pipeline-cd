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

Generating and validating hashes

* Linux built-in: ```shasum```
* Use SHA-256: ```shasum -a 256 [file]```
* Write it to a file: ```shasum -a 256 [file] > [hash file]```
* Compare a file to its hash: ```shasum -c [hash file]```
  * If the file and its hash match, returns ```[file]: OK```
* Compare two hash files: ```cmp [hashfile1] [hashfile2]```
  * If identical, returns nothing

But... ```shasum``` doesn't work on a directory
<details>
  <summary> Options? </summary>
  * Compute hash on each compiled binary
     * Ideally we only compute one hash
  * Zip directory, then hash compressed file
     * tar -zf archive-name.tar.gz source-directory
     * where:
       * ```-z``` uses gzip program for compression
       * ```-c``` create archive (rather than append)
       * ```-f``` archive path and file name
</details>



[Next slide](lessons_outcomes.md)
