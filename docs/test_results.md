# Acceptance and verification results

This file records verification performed during Mapterhorn terrain support
and `splat-batch` development. Numbers are from those runs only. Items that
were not completed are marked as such.

How to run the automated unit suite and sanitizers is described in
[TESTING.md](../TESTING.md).

## Unit tests

- **306 passed**, **3 skipped**
- Skips: PPD stubs and no GDAL GeoTIFF support in the test environment

## Mapterhorn / WebP terrain

- WebP tiles confirmed **lossless** Terrarium-encoded elevation (as used by
  Mapterhorn)
- SDF tile **60/10** (page `60_61_349_350`): header and lake/summit checks for
  Tyrifjorden, Randsfjorden, Lushaugen, and Skreikampen passed
- Path-loss comparison at **145 MHz**: SRTM/Skadi vs Mapterhorn within about
  **1.3 dB**
- Builds **without** `-mapterhorn`: output **byte-identical** to unpatched HEAD

## Despike (`mapterhorn2sdf`)

- Randsfjorden spike reduced from **494 m** to **133 m**
- Real summits on the 60/10 page preserved (not clipped relative to
  `--no-despike`)

## splat-batch

- Dry-run on `repeaters.joz`: **236 jobs** / **245 skips**
- SD vs HD hear area on four hilly sites: about **+0.1% to +3.9%** (SD larger)
- ITM coverage error reporting: paths under 2 km ignored; error **3** counted
  in the run report; errors **>= 4** fail the job
- **Full national 236-job production run was not completed** (stopped). Scope
  of the production attempt was the LA5MR network only.

## Not verified / not claimed

- A completed end-to-end national batch of all 236 jobs
- Long-duration production stability metrics beyond the checks above

Attribution for Mapterhorn terrain data:
https://mapterhorn.com/attribution
