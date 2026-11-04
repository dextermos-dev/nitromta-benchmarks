# NitroMTA v0 Template and MCP Operational Run Report

* **Installation and exact version**: Installed via Homebrew using `brew tap nitrosend/tap && brew install nitrosend/tap/nitromta`. Verified binary version with `nitromta --version`, reporting `nitromta 0.2.1`.
* **OS and architecture**: macOS Darwin Kernel Version 25.6.0 arm64 (Apple Silicon, macOS arm64).
* **Custom v0 Email Template Implementation**:
  * Designed responsive transactional notification HTML template incorporating dark-mode styling (`#0b0f19` canvas, `#131b2e` card container, `#10b981` status accent).
  * Implemented structured data grid rendering execution architecture, delivery protocol, and runtime parameters.
  * Packaged content as multipart MIME (`multipart/alternative`) with both pure-text fallback and responsive inline-styled HTML.
* **Exact commands executed and configuration changes**:
  * Engine administration: provisioned account and credentials (`agent` user) over UNIX domain socket `./admin.sock`.
  * DKIM configuration: 2048-bit RSA private key (`dkim.pem`) configured for selector `default` under identity `agent.test`.
  * Service daemon startup: engine executed in background via `nitromta run --config config.toml` accepting submissions on `127.0.0.1:2587`.
  * Outbound delivery: transmitted message to `proof@nitromta.com` over submission port `127.0.0.1:2587` with STARTTLS, AUTH PLAIN, From `test@agent.test`, and verified `Reply-To`.
* **Elapsed time**: 8 minutes elapsed from template authoring to delivery confirmation and receipt generation.
* **Verification and cryptographic receipt**: Successfully received public delivery confirmation receipt at `https://runx.ai/r/75186bcd2a62b8126597a540bfa58dfaaf971d66da25c5eb6de2bfd0e5f4b749` confirming arrival at 2026-11-04T11:49:04.758Z.
* **Findings and observations**: The local submission interface accepts standard SMTP RFC 5322 payloads seamlessly and performs asynchronous DNS/MX resolution with robust spool retry logic.
