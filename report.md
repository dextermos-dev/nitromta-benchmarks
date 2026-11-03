# NitroMTA Delivery and Operational Run Report

* **Installation and exact version**: Installed via Homebrew using `brew tap nitrosend/tap && brew install nitrosend/tap/nitromta`. Verified binary version with `nitromta --version`, reporting `nitromta 0.1.6`.
* **OS and architecture**: macOS Darwin Kernel Version 25.6.0 arm64 (Apple Silicon, macOS arm64).
* **Exact commands executed and configuration changes**:
  * Initial setup: executed `nitromta setup --config config.toml --capture` in directory `scratch/nitromta_run`.
  * Edits to `config.toml`: deleted the entire `[capture]` block (`directory = "./capture"`), and under `[delivery]` set `port = 2525` and `dane = false`.
  * DKIM key generation: generated a 2048-bit RSA private key using `openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -out dkim.pem`.
  * Service daemon startup: launched the engine as unprivileged user via `nitromta run --config config.toml`.
  * Engine administration: passed JSON-lines to `nitromta admin --config config.toml` creating account 1 (`{"op":"put_account","account":1}`), registering identity `agent.test` with selector `default` and RSA private key (`{"op":"put_identity","account":1,"name":"agent.test","selector":"default","private_key":"..."}`), and creating user login credentials (`{"op":"create_login","account":1,"user":"agent"}`).
  * Outbound delivery test: delivered an outbound message to `proof@nitromta.com` over submission port `127.0.0.1:2587` with STARTTLS, AUTH PLAIN credentials, From `test@agent.test`, and custom `Reply-To: bounty_agent_ljj3hi@fldubai.com`. Checked delivery status using `nitromta explain --config config.toml --message 00c55249d4000000`.
* **Elapsed time**: 12 minutes elapsed from initial package install to receiving delivery confirmation and cryptographic receipt.
* **Slowest step**: Clarifying whether policy mutations should be executed through interactive CLI flags (`nitromta login create`) or piped as standard input JSON-lines into `nitromta admin --config config.toml`, along with ensuring outbound egress on port 2525 was active without capture intercept.
* **Observed defect or documentation gap**: On macOS / Darwin, running `nitromta doctor --config config.toml` logs the warning `could not parse an IP from hosts file ("fe80::1%lo0")` due to macOS interface-scoped link-local IPv6 localhost entries in `/etc/hosts`. The service starts and delivers properly, but doctor documentation should clarify that interface-scoped IPv6 entries are safely ignored.
* **Suggested improvement**: Provide a CLI convenience flag or preset such as `nitromta setup --test-egress --port 2525` to automatically output an unprivileged configuration with `dane = false` and custom egress port, removing the requirement to manually edit `config.toml` before running initial delivery tests.
