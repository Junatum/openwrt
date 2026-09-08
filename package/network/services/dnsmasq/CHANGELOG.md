# Changelog

## 2.93-r2 - 2026-09-08

### Added

- Add SafeShield in-memory cumulative DNS query counters.
- Add bounded per-client query/block counters (128 clients).
- Add `instance_id` so collectors can detect dnsmasq restarts.
- Add the `safeshield_stats` UBus method for low-frequency polling.
- Add `safeshield-block=/domain/` for rules that must be counted as SafeShield blocks.

### Notes

- Counters intentionally remain in RAM and are reset when dnsmasq restarts.
- The initial PoC counts the normal UDP DNS path; the UBus response reports `transport_scope: udp` explicitly.
