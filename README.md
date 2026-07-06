# pg_wtf

A tiny troubleshooting script for when a Homebrew-installed PostgreSQL won't start on macOS, usually after a hard crash or reboot leaves a stale lock file behind.

Instead of remembering the incantations each time, `pg_wtf` does it for you:

1. Tails the Postgres log file for the most recent errors.
2. Reads the `postmaster.pid` file and checks whether the referenced process is actually a Postgres instance (a stale PID file is a common reason it won't restart).
3. Prints the relevant `brew` commands for inspecting, stopping, and starting the service.

It only **reads** and reports — it never deletes the PID file or restarts anything for you.

## Usage

```sh
./pg_wtf
```

## Configuration

Postgres paths differ by version and install. Open the script and set `LOGFILE` and `PIDFILE` to match your setup — it ships with sensible Homebrew defaults and commented alternatives for older Postgres versions.

## Requirements

- macOS with PostgreSQL installed via Homebrew.

> Written to scratch a specific itch; paths are hardcoded and may need tweaking for your Postgres version.
