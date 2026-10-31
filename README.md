# ns2-assets

the content side of ns2-savekit: decode a dumped romfs tree (BFRES models,
BNTX textures), export mario kart world geometry, and build the 40x69 artwork
set the in-game chooser reads.

split out so the save kit stops carrying it. history is preserved: `git log`
here goes back to the original commits.

## what's here

- `tools/asset-triage.py` — classify a dumped tree by container magic before
  decoding anything.
- `tools/bfres10.py`, `bfres10_anim.py` — BFRES v10 model/skeleton/animation.
- `tools/bntx_batch.py`, `bntx_decode.py`, `bntx_ounce.py` — BNTX textures.
- `tools/mkw_export.py` — mario kart world geometry export.
- `tools/artwork-build.cjs` — build the artwork blobs + index for
  `payloads/ns2jb-artwork.lua`.
- `payloads/ns2jb-artwork.lua`, `payloads/ns2jb-map.lua` — the in-game
  chooser payloads.
- `docs/ANIM-FSKA.md`, `ASSETS.md`, `BFRES-V10.md`, `TEXTURES-MKW.md`.

you need a dump to point the tools at. dumping romfs is the console side:
`ftp-mirror.py` lives in [ns2-console](https://github.com/dougchansan/ns2-console),
and the save/launch tooling is [ns2-savekit](https://github.com/dougchansan/ns2-savekit).

## tests

```sh
lua tests/test_artwork_lua.lua      # chooser selection (needs payloads/ns2jb-metadata.lua)
python3 tools/asset-triage.py --help
```
