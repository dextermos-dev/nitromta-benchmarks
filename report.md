# NitroMTA Delivery and Operational Run Report

* **Installation and exact version**: Installed via Homebrew using . Verified binary version with nitromta 0.1.6, reporting .
* **OS and architecture**: macOS Darwin Kernel Version 25.6.0 arm64 (Apple Silicon, macOS arm64).
* **Exact commands executed and configuration changes**:
  * Initial setup: executed  in an isolated directory.
  * Edits to : deleted the  block (), and configured  parameters with OS platform mismatch
    while executing
"mportinit ui_options global_options global_variations" and .
  * DKIM key generation: generated a 2048-bit RSA private key using .
  * Service daemon: launched the engine via .
  * Engine administration: passed operations to  creating account 1 (), registering identity  with selector  and the generated RSA private key (), and provisioning credentials ( for user ).
  * Outbound delivery test: delivered an outbound message to  over submission port  with STARTTLS, AUTH PLAIN, From , and Reply-To header. Checked delivery resolution using .
* **Elapsed time**: 12 minutes elapsed from initial package install to receiving delivery confirmation and cryptographic receipt.
* **Slowest step**: Clarifying whether policy mutations should be executed through interactive CLI flags or standard input JSON-lines into , along with ensuring outbound egress on port 2525 was active without capture intercept.
* **Observed defect or documentation gap**: On macOS / Darwin, running  logs a warning  due to macOS interface-scoped IPv6 localhost entries in . The service starts and delivers properly, but doctor output could document that interface-scoped link-local IPv6 entries are safely ignored.
* **Suggested improvement**: Provide a CLI convenience flag or preset such as  to quickly scaffold non-root direct testing environments without requiring manual edits to .
