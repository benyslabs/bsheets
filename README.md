# bSheets

A desktop spreadsheet for Excel power users, built on a Rust engine. It works differently from Excel underneath, but the shortcuts, behaviour and file formats are close enough that moving over should feel familiar.

**Status: early access (alpha).** Things change quickly and files from one build may not open in the next. Keep backups.

## Download

Get the latest installer from [Releases](https://github.com/benyslabs/bsheets/releases/latest): `bSheets_<version>_x64-setup.exe`, Windows 10 or 11, 64-bit.

The installer is not code-signed yet, so Windows SmartScreen may say "Windows protected your PC". Choose **More info**, then **Run anyway**. Each release lists the installer's SHA-256 so you can check the download.

## What's in it

- Grid sheets with their own formula language, plus columnar table sheets that stay responsive at 10 million rows
- Pivots, measures, charts and Pages (print and PDF layouts)
- Import of `.xlsx`, Power Query M, DAX measures and VBA, with an import report for anything that did not carry over
- Data sources: files, SQL Server, PostgreSQL, MySQL and more, with credentials held in the Windows credential store
- Scripting (JavaScript), a local Python runner, a `bsheets` CLI and an MCP server for agents
- Built-in help and guides

## Licence

Free for personal use, and free for commercial use during early access. bSheets is not open source; this repository holds releases only. Full terms: [LICENSE.md](LICENSE.md). Third-party components: [THIRD_PARTY.md](THIRD_PARTY.md).

## Feedback

Bug reports and ideas are welcome in [Issues](https://github.com/benyslabs/bsheets/issues). A small sample file and the steps to reproduce help most. Using bSheets at work? Say so in an issue; it helps decide what comes next.

Copyright (c) 2026 Benys Labs. All rights reserved.
