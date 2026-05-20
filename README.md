# xchf (Deprecated)

> **This project has been deprecated.** Please use [tttne](https://github.com/haoli000/tttne) instead.

`xchf` has been merged into `tttne`, which now supports all 3GPP TS 32.298 CDR types (CHF, GPRS, IMS, CS, SMS, and more).

## Migration

Install `tttne`:

```bash
curl -L https://raw.githubusercontent.com/haoli000/tttne/main/install.sh | bash
```

Usage is the same:

```bash
tttne cdr.bin          # YAML output
tttne cdr.bin --json   # JSON output
```

See the [tttne repository](https://github.com/haoli000/tttne) for full documentation.
