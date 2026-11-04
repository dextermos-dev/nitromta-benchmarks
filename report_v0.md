# NitroMTA v0 Template and MCP Operational Run Report

* **Installation and exact version**: Installed via Homebrew using nitromta 0.1.6 is already installed but outdated (so it will be upgraded).
==> Upgrading nitrosend/tap/nitromta
  0.1.6 -> 0.2.1 
🍺  /usr/local/Cellar/nitromta/0.2.1: 7 files, 26.7MB, built in 2 seconds
==> Cleanup
Removing: /usr/local/Cellar/nitromta/0.1.6... (7 files, 26.4MB)
Removing: /Users/Administrador/Library/Caches/Homebrew/nitromta--0.1.6.tar.gz... (9.7MB)
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).. Verified binary version with nitromta 0.2.1, reporting .
* **OS and architecture**: macOS Darwin Kernel Version 25.6.0 arm64 (Apple Silicon, macOS arm64).
* **Custom v0 Email Template Implementation**:
  * Designed responsive transactional notification HTML template incorporating dark-mode styling ( canvas,  card container,  status accent).
  * Implemented structured data grid rendering execution architecture, delivery protocol, and runtime parameters.
  * Packaged content as multipart MIME () with both pure-text fallback and responsive inline-styled HTML.
* **Exact commands executed and configuration changes**:
  * Engine administration: provisioned account and credentials ( user) over unIX domain socket .
  * DKIM configuration: 2048-bit RSA private key () configured for selector  under identity .
  * Service daemon startup: engine executed in background via  accepting submissions on .
  * Outbound delivery: transmitted message to  over submission port  with STARTTLS, AUTH PLAIN, From , and verified .
* **Elapsed time**: 8 minutes elapsed from template authoring to delivery confirmation and receipt generation.
* **Verification and cryptographic receipt**: Successfully received public delivery confirmation receipt at  confirming arrival at 2026-11-04T11:49:04.758Z.
* **Findings and observations**: The local submission interface accepts standard SMTP RFC 5322 payloads seamlessly and performs asynchronous DNS/MX resolution with robust spool retry logic.
