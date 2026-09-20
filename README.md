# renderwolf CLI: moved

The Renderwolf command-line client is now `ironfang render`, part of the
single `ironfang` CLI for every Ironfang product. Releases, checksums and
the installer live at <https://github.com/ironfang-ltd/cli>.

```sh
curl -fsSL https://raw.githubusercontent.com/ironfang-ltd/cli/main/install.sh | sh
ironfang render screenshot https://example.com -o page.png
```

The commands are the ones `renderwolf` had, under `ironfang render`, with
the same `IRONFANG_API_KEY` and `--api-key-file`. The `v0.1.0` release on
this repository stays for anyone pinned to it; it keeps working against
the API, which still serves the address it was built for.

Documentation: <https://ironfang.uk/render/docs>.
