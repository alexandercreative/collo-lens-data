# collo-lens-data

A subset of the lensfun lens database, converted to JSON. This is the exact data file that the Collo RAW developer
(by Alexander Creative) bundles as a fallback for lens corrections. It is published here, free to download and reuse,
under the same licence as the original: **Creative Commons Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0)**.

Date: 2026-10-23

## Credit

- **Title:** the lensfun lens database (`data/db`)
- **Authors:** the lensfun contributors, building on the PTLens lens database by Thomas (Tom) Niemann
  (http://www.epaperpress.com/ptlens/), which lensfun's database grew from with his permission
- **Source:** https://github.com/lensfun/lensfun
- **Licence:** CC BY-SA 3.0, https://creativecommons.org/licenses/by-sa/3.0/ (the full legal code is in [`LICENSE`](LICENSE))
- **Changes:** this is a modified, adapted subset, see below. It was converted to JSON by Alex Goeke (Alexander Creative).

Lens correction data: adapted from the lensfun lens database by the lensfun contributors
(https://github.com/lensfun/lensfun), licensed under CC BY-SA 3.0 (https://creativecommons.org/licenses/by-sa/3.0/).
Changes: a subset of the database, converted to JSON by Alex Goeke (Alexander Creative). The adapted data is licensed
under CC BY-SA 3.0 and is free to download at https://github.com/alexandercreative/collo-lens-data. Provided "as is",
without warranties.

The lensfun authors did not make or endorse this subset and are not affiliated with Collo or Alexander Creative.

## What is in here

| File | What it is |
|---|---|
| `lensfun.json` | The adapted data (730,529 bytes, SHA-256 `87b60d705602f43ab90bf26ea00ace6285acefffb8627695fae9de284a18d366`). |
| `LICENSE` | The CC BY-SA 3.0 Unported legal code, as shipped with lensfun (`data/COPYING.CC_BY-SA_3.0`). |
| `README.md` | This file. |

## Changes made to the original (CC BY-SA 3.0 section 3(b))

The original is a folder of XML files. The changes are:

1. **A subset.** 256 lenses and 737 cameras, out of the full database. For each of nine makers (Canon, Nikon, Fujifilm, Sony, Leica,
   Panasonic or Lumix, OM or Olympus, Sigma, Tamron) the 20 best-covered lenses were kept (a common zoom range or prime, vignetting data,
   distortion data, several focal lengths calibrated), plus every lens that appears in Collo's own reference photo sets. The cameras of those
   makers were kept as (maker, model, crop factor) so a lens can be matched to a sensor size.
2. **Converted from XML to JSON.** Each lens keeps its maker, model name, aliases, mount, crop factor, aspect ratio, and its raw
   calibration entries: distortion (ptlens, poly3 or poly5, per focal length), transverse chromatic aberration (poly3 or linear, per
   focal length) and vignetting (`pa` model, per focal length, aperture and focus distance).
3. **No values were recalculated.** The numbers are lensfun's own, with the same units: distortion in Hugin coordinates (r = 1 at half the short side
   of the calibration frame), vignetting with r = 1 at the calibration frame's corner. Collo converts them to its own coordinates when it reads them.
4. **A header.** The JSON carries `"version": 1` and a `"source"` string naming lensfun and its licences.

Collo does not use the lensfun library (which is LGPL-3), only this data.

## How it is used

Collo uses it only where the camera maker's own lens profile has no vignetting or distortion data for a lens. It never replaces a profile the maker supplies.

## Licence and sharing

The adapted data in this repository is licensed under CC BY-SA 3.0, the same licence as the lensfun database. You may copy, share and adapt it,
including commercially, if you credit the sources above, say what you changed, and share your adaptation under CC BY-SA 3.0 (or a compatible licence).
The licence covers this data only. It does not cover the Collo app or anything else made by Alexander Creative.

Questions: creative@alexandergoeke.com
