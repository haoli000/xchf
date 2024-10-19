# xchf

`xchf` is a command-line interface (CLI) tool designed to decode CHF (Charging Function) records (with record type 200) as defined in 3GPP TS 32.298. The current implementation is based on version 18.5.0 of the specification.

## Overview

This tool allows users to decode and analyze CHF records, which are crucial for billing and charging in mobile networks. It provides a simple interface to process these records and output the results in various formats.

## Installation

### Install Script

Download `xchf` and install into a local bin directory.

#### MacOS, Linux, WSL

Latest version:

```bash
curl -L https://raw.githubusercontent.com/haoli000/xchf/main/install.sh | bash
```

Specific version:

```bash
curl -L https://raw.githubusercontent.com/haoli000/xchf/main/install.sh | bash -s 0.4.0
```

The script will install the binary into `$HOME/bin` folder by default, you can override this by setting
`$CUSTOM_INSTALL` environment variable

### Manual download

Get the archive that fits your system from the [Releases](https://github.com/haoli000/xchf/releases) page and
extract the binary into a folder that is mentioned in your `$PATH` variable.

## Usage

```bash
xchf [file|-] [flags]
```

The tool can read from a file or from standard input (using `-`).

## Flags

- `-h, --help`: Display help information for xchf
- `-j, --json`: Output the results in JSON format
- `-v, --verbose`: Increase output verbosity. Can be used multiple times for increased verbosity levels

## Examples

1. Decode a CHF CDR and output in YAML format:

   ```bash
   xchf cdr.bin
   ```

2. Decode a CHF record file and output in JSON format:

   ```bash
   xchf cdr.bin --json
   ```

3. Decode a CHF record from standard input with increased verbosity:

   ```bash
   cat cdr.bin | xchf -vv
   ```

4. Use `xchf` with output from [`tttns`](https://github.com/haoli000/tttns):

   ```bash
   cat ts_32297_cdrs.bin | tttns cdr dump 1 | xchf
   ```

   This command pipeline does the following:
   - `cat ts_32297_cdrs.bin`: Outputs the content of the CDR file
   - `tttns cdr dump 1`: Uses the [`tttns`](https://github.com/haoli000/tttns) tool to dump the first CDR record
   - `xchf`: Decodes the CHF record from the output of [`tttns`](https://github.com/haoli000/tttns)

## Verbosity Levels

The `-v` flag can be used multiple times to increase the verbosity of the output:

- No `-v`: Basic output
- `-v`: Detailed output
- `-vv`: More detailed output
- `-vvv`: Most detailed output (debug level)

## Output Formats

By default, `xchf` outputs in YAML format. Use the `-j` or `--json` flag to output in JSON format, which can be useful for further processing or integration with other tools.

## Compatibility

This tool is implemented based on 3GPP TS 32.298 version 18.5.0.

## Integration with Other Tools

As demonstrated in Example 4, `xchf` can be effectively used in combination with other tools like `tttns`. This allows for powerful data processing pipelines, where you can extract specific CDR records using `tttns` and then decode them using `xchf`.

## Disclaimer

This tool is provided as-is. Users should ensure they have the necessary rights and permissions to decode and analyze CDRs in their possession.

## Notes

The project has been scaffolded with the help of [kleiner](https://github.com/can3p/kleiner).
