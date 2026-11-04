# Third-party code

- IronCalc (https://github.com/ironcalc/IronCalc), MIT OR Apache-2.0. Function bodies and test cases in `crates/bsheets-functions` marked `harvested from IronCalc` in their header comment are adapted from `base/src/functions`. Copyright the IronCalc authors. The finance bodies (`daycount.rs`, `loans.rs`, `depreciation.rs`, `securities.rs`) are IronCalc's ports of ExcelFinancialFunctions (https://github.com/fsprojects/ExcelFinancialFunctions, Apache-2.0), reshaped to this function trait.
- Natural Earth (https://www.naturalearthdata.com), public domain. `assets/maps/world.json` is built from the 1:110m Cultural Vectors "Admin 0 - Countries" layer (Antarctica dropped) and `assets/maps/au-states.json` from the 1:50m "Admin 1 - States, Provinces" layer (Australia only, Jervis Bay Territory and outlying islands dropped), both via the GeoJSON copies in https://github.com/nvkelso/natural-earth-vector. Simplified with mapshaper (Visvalingam weighted, keep-shapes, 70% and 60% of points retained) and packed by `scripts/maps/pack_map.py`; steps in `docs/maps.md`. The first-level regions (`assets/maps/admin1.json`, every country with Natural Earth admin-1 data, 239 layers) come from the 1:10m "Admin 1 - States, Provinces" layer, simplified by `scripts/maps/simplify_admin1.py` (Douglas-Peucker, shared borders kept in step) and packed by `scripts/maps/pack_map_set.py`. Made with Natural Earth.
- Oxc (https://github.com/oxc-project/oxc), MIT. `oxc_allocator`, `oxc_ast`, `oxc_ast_visit`, `oxc_codegen`, `oxc_diagnostics`, `oxc_parser`, `oxc_semantic`, `oxc_span` and `oxc_transformer`, one release line pinned together (`=0.153.0`), are dependencies of `crates/bsheets-ext` (feature `typescript`): they parse a TypeScript script and strip its types. No Oxc source is copied. Copyright the Oxc contributors (transitive dependencies carry their own notices).
- The `typescript` npm package (https://github.com/microsoft/TypeScript), Apache-2.0, a development dependency of `apps/desktop`: the script editor's advisory type check runs the compiler and the ECMAScript library declarations from it in a web worker. Copyright Microsoft Corporation.
- Crates used by `crates/bsheets-xlsx` (dependencies, not vendored code): `zip` (MIT), `quick-xml` (MIT), `base64` (MIT OR Apache-2.0), `calamine` 0.36 (MIT; reads .xls and .xlsb, copyright Johann Tuffe and the calamine contributors), `resvg` (Apache-2.0 OR MIT, draws an icon's PNG fallback; already in the lock through krilla-svg).
- `ripbi-xpress9` 0.13.0 (https://github.com/bgarcevic/ripbi), MIT OR Apache-2.0, a dependency of `crates/bsheets-xlsx`. It vendors Microsoft's XPress9 library (Copyright (c) Microsoft Corporation, MIT, microsoft/Extensible-Storage-Engine `dev/ese/src/_xpress9`) through the GCC port in https://github.com/Hugoberry/xpress9-python (MIT, Copyright (c) 2025 Igor Cotruta). The XPress8 decoder in `crates/bsheets-xlsx/src/mashup/xpress.rs` follows the format in the same repository's `dev/ese/src/_xpress` (MIT).
- PBIXRay test data (https://github.com/Hugoberry/pbixray), MIT, Copyright (c) Igor Cotruta. `crates/bsheets-xlsx/tests/fixtures/powerpivot` holds its `null_data_id.xlsx` and `Supplier Quality Analysis Sample-no-PV.xlsx` (`supplier-quality.xlsx` here, a test-only file, not shipped; it derives from Microsoft's Power BI Supplier Quality sample, https://github.com/microsoft/powerbi-desktop-samples, MIT); the two `.xp9` files wrap the first one's model in the XPress9 stream.
- PyO3 (https://github.com/PyO3/pyo3), MIT OR Apache-2.0, the Python bindings of `crates/bsheets-py`.
- Crates used by `crates/bsheets-engine` for password to open (dependencies, not vendored code; the RustCrypto project, MIT OR Apache-2.0): `argon2` (Argon2id key derivation, with `blake2` and `password-hash`), `aes-gcm` (AES-256-GCM, with `aes`, `ghash` and `cipher`), `hmac` (HMAC-SHA256 part names over the existing `sha2`), `zeroize` (Apache-2.0 OR MIT; wipes keys) and `getrandom` (MIT OR Apache-2.0; the system random source, already in the lock).
- Natural Earth (https://www.naturalearthdata.com), public domain. The bundled map outlines in `assets/maps` (world countries, Australian states and the first-level regions of every country that has them) are simplified Natural Earth shapes; no permission or attribution is required, and it is credited here anyway.
- Lucide (https://lucide.dev), ISC, with the Feather icons it derives from under MIT (Cole Bemis). `crates/bsheets-engine/assets/icons.tsv` is built from the `lucide` npm package 1.8.0 by `apps/desktop/scripts/icons-data.mjs`: the vector icons of Insert > Icons. Copyright (c) 2026 Lucide Icons and Contributors. Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies. THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS.
- Tabler Icons (https://tabler.io/icons), MIT, Copyright (c) Pawel Kuna. Heroicons (https://heroicons.com), MIT, Copyright (c) Refactoring UI Inc. Flat Color Icons (https://github.com/icons8/flat-color-icons), MIT, Copyright (c) Icons8. `crates/bsheets-engine/assets/icons-tabler.tsv`, `icons-heroicons.tsv` and `icons-flat-color.tsv` are built from the `@iconify-json` npm packages (tabler 1.2.43, heroicons 1.2.3, flat-color-icons 1.2.3) by `apps/desktop/scripts/icon-packs-data.mjs`: the extra icon sets of Insert > Icons. Full licence text in `THIRD_PARTY_LICENSES.txt`.
- Crates used by `crates/bsheets-sources` for the file connectors (dependencies, not vendored code): `calamine` (MIT; reads another Excel workbook's sheets, tables and defined names), `pdf-extract` (MIT; text and positions from a PDF, with its `lopdf` dependency, MIT), `roxmltree` (MIT OR Apache-2.0; XML trees), `encoding_rs` (MIT OR Apache-2.0 and BSD-3-Clause; text encodings).
- GridCraft (https://github.com/storytold/gridcraft), MIT OR Apache-2.0. The xlsx writer's chart element order (`crates/bsheets-xlsx/src/export/chart.rs`), the minimal theme part shape (`export/theme.rs`) and the dynamic array metadata part follow GridCraft's `crates/xlsx` writer. Copyright the ArtCraft Team and the GridCraft contributors.
- Native document export dependencies (not vendored code): `krilla` 0.8.2 and `krilla-svg` 0.8.1 (MIT OR Apache-2.0), `cosmic-text` 0.19 (MIT OR Apache-2.0), `usvg` 0.47 (Apache-2.0 OR MIT), `fontdb` 0.23 (MIT). The glyph adapter follows the API patterns in krilla's `examples/parley.rs` and its text, annotation, outline and SVG documentation. No upstream source file or font asset is copied. System/user font files are embedded only when their embedding flags permit it; bundled fonts have a separate future hook.
- SCOWL (Spell Checker Oriented Word Lists, http://wordlist.aspell.net, https://github.com/en-wl/wordlist), size 60, Australian (`assets/dictionaries/en-AU.txt`) and American (`assets/dictionaries/en-US.txt`) English, generated once offline with the SCOWL list tool (max size 60, variants 0, diacritics stripped, the hacker list included), one word per line, UTF-8. Copyright Kevin Atkinson and the other SCOWL contributors; permissive licence (permission to use, copy, modify, distribute and sell with the copyright and permission notice kept). The notice ships verbatim as `assets/dictionaries/SCOWL-LICENSE.txt` beside the lists. Used by spell check in the engine, desktop and CLI.
- Carlito (https://github.com/googlefonts/carlito), SIL Open Font License 1.1. `assets/fonts/Carlito-Regular.ttf`, `-Bold`, `-Italic` and `-BoldItalic` are the upstream font files, unmodified, bundled with PDF export (`crates/bsheets-export`) and the desktop app as the app's default font and the always-used, metric-compatible face for Calibri (UI, formula bar, charts, pages and PDF export; the font is never altered or sold on its own). Copyright 2013 The Carlito Project Authors (https://github.com/googlefonts/carlito), with Reserved Font Name "Carlito" (the font files' name tables and `OFL.txt` say the same); Carlito is a Lato derivative by Google. The licence ships verbatim as `assets/fonts/OFL.txt`. The fonts are not sold on their own.
- Apache POI test data (https://poi.apache.org), Apache-2.0. `crates/bsheets-vba/tests/fixtures/oforms` holds `31979.xls` and UserForm storages copied out of `15556.xls`, `31749.xls` and `59858.xls` from POI's spreadsheet test data, used as test inputs for the UserForm designer reader (details in that folder's README).
- calamine test data (https://github.com/tafia/calamine), MIT, copyright Johann Tuffe and the calamine contributors. `crates/bsheets-sources/tests/fixtures/workbooks` holds `date.xls`, `date.xlsb`, `any_sheets.xls` and `any_sheets.xlsb` copied from calamine's `tests` folder, used as inputs for the linked workbook source tests (`small.ods` there is our own, copied from `crates/bsheets-xlsx/tests/fixtures`).


## Carlito: SIL Open Font License 1.1 (full text)

Copyright 2013 The Carlito Project Authors (https://github.com/googlefonts/carlito), with Reserved Font Name "Carlito"


This Font Software is licensed under the SIL Open Font License, Version 1.1.
This license is copied below, and is also available with a FAQ at:
https://scripts.sil.org/OFL


-----------------------------------------------------------
SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007
-----------------------------------------------------------

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded, 
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF THE USE OR INABILITY TO USE THE FONT SOFTWARE OR FROM
OTHER DEALINGS IN THE FONT SOFTWARE.
- w16 entry: `spellbook` 0.4 (https://github.com/helix-editor/spellbook), MPL-2.0, a Hunspell reader used as a dependency of `bsheets-engine`, unmodified. `icu_calendar` 2.3 and its compiled data (ICU4X, https://github.com/unicode-org/icu4x), Unicode-3.0, convert dates for the Hijri (Umm al-Qura), Hebrew, Japanese, Thai Buddhist and Taiwan calendars. Dictionaries bundled from `crates/bsheets-engine/dict/` (SCOWL-based, MIT AND BSD) are listed in `crates/bsheets-engine/dict/LICENSES.md`; the AutoCorrect seed list `assets/autocorrect/en.json` is original to this project.

- Bundled dictionaries en-GB (-ise) and en-CA (`crates/bsheets-engine/dict`): Hunspell dictionaries from the SCOWL-based wooorm/dictionaries packages (MIT AND BSD), each with its licence file beside it; never LibreOffice's LGPL en_GB. `spellbook` (MPL-2.0) is used unmodified from crates.io.

## Licence notices for a release

`THIRD_PARTY_LICENSES.txt` at the repo root holds the full copyright and licence texts of everything that ships (Rust crates, npm packages, fonts, icons, maps, word lists, dictionaries, adapted code). It is generated by `scripts/licences/build.mjs` (see `scripts/licences/README.md`), built into the app for Help > About > Third-party licences and installed beside the exe. MPL-2.0 crates (cssparser, selectors, dtoa-short and friends) are used unmodified and list their source URL there.
