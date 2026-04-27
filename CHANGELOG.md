# Changelog

## 1.0.0

### Added

- Initial release of `Sqlite.Migrate`: apply ordered SQL migrations to a SQLite
  database, secured by a hash chain.
- `preview` for reporting which migrations would be applied without applying
  them.
- Transaction-safe application via SQLite savepoints, composing with
  caller-owned transactions.
- A detailed `Error` type covering empty or conflicting migrations, chain
  divergence, hash mismatches, and base64 decoding failures.
