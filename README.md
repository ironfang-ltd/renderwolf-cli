# Renderwolf CLI

The Renderwolf rendering API from the command line: screenshots, PDFs, QR
codes, clips and site previews, rendered on Ironfang's UK infrastructure.

```
renderwolf screenshot https://example.com --full-page -o page.png
renderwolf pdf --html invoice.html --paper a4 -o invoice.pdf
renderwolf qr "https://ironfang.uk" --size 512 -o code.png
renderwolf job submit request.json --wait -o result.bin
renderwolf history --since 24h
renderwolf usage
```

## Install

Download the archive for your platform from
[Releases](https://github.com/ironfang-ltd/renderwolf-cli/releases), verify
it against `checksums.txt`, then put the binary on your PATH:

```
tar -xzf renderwolf_v0.1.0_linux_amd64.tar.gz
sudo mv renderwolf_v0.1.0_linux_amd64/renderwolf /usr/local/bin/
renderwolf version
```

macOS (Intel and Apple Silicon) and Windows builds are in the same release.

## Authentication

Create an API key in the [portal](https://portal.ironfang.uk), then either
export it or point the CLI at a file that holds it:

```
export IRONFANG_API_KEY=if_live_...
# or
renderwolf screenshot https://example.com --api-key-file ~/.config/ironfang/key -o page.png
```

The key is never accepted as a command-line argument, so it stays out of
shell history and process lists.

## Commands

| Command | What it does |
| --- | --- |
| `screenshot <url>` | Capture a page as PNG, JPEG or WebP; `--full-page`, `--device mobile` |
| `pdf <url> \| --html file` | Render a page or your own HTML to PDF; `--paper`, `--landscape` |
| `qr <data>` | Generate a QR code; every code is decoded to verify it before delivery |
| `clip --json clip.json` | Produce a captioned MP4 clip |
| `job submit\|get\|wait\|cancel\|result` | Work with durable render jobs |
| `history` | Your recent requests; `--failed`, `--kind`, `--since` |
| `usage` | Credits used this period |
| `doctor` | Check connectivity and key validity |

Every render command also takes `--json <file>` for the full request body
and `--request-id <id>` for your own correlation id. `--verbose` prints
request and response headers with secrets redacted.

## Pricing

Commands spend ordinary Renderwolf credits - a screenshot is one credit, a
PDF is two, QR codes are free, cached repeats are free, and failed work is
refunded. Accounts start with 250 free credits a month, no card required.

Docs: https://ironfang.uk/renderwolf/docs
