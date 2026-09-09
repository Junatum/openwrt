# Changelog

## 2.93-r3 - 2026-09-09

### Added

- Account client-originated DNS-over-TCP queries in SafeShield cumulative statistics.
- Forward TCP query and blocked deltas from dnsmasq TCP child processes to the parent through the existing child-to-parent pipe.
- Preserve global and per-client query/blocked counters across TCP child process exit without shared memory or locks.

### Changed

- Report `transport_scope` as `udp+tcp` from the `safeshield_stats` UBus method.

### Notes

- TCP accounting covers DNS clients connecting to dnsmasq over TCP; upstream TCP fallback and internal DNSSEC TCP work are not counted as new client queries.

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
