# Third-party notices: bioio

This container installs [bioio](https://github.com/bioio-devs/bioio) and a
set of format-reader plugins via pip, pinned to the exact versions in
[requirements.txt](requirements.txt).

## Licenses

| Package | License | Source |
|---|---|---|
| bioio | BSD-3-Clause | https://github.com/bioio-devs/bioio |
| bioio-base | BSD-3-Clause | https://github.com/bioio-devs/bioio-base |
| bioio-czi | GPL-3.0 | https://github.com/bioio-devs/bioio-czi |
| bioio-lif | GPL-3.0 | https://github.com/bioio-devs/bioio-lif |
| bioio-nd2 | BSD-3-Clause | https://github.com/bioio-devs/bioio-nd2 |
| bioio-ome-tiff | BSD-3-Clause | https://github.com/bioio-devs/bioio-ome-tiff |
| bioio-ome-zarr | BSD-3-Clause | https://github.com/bioio-devs/bioio-ome-zarr |
| bioio-tifffile | BSD-3-Clause | https://github.com/bioio-devs/bioio-tifffile |

`bioio-czi` additionally depends on
[aicspylibczi](https://github.com/bioio-devs/aicspylibczi), also GPL-3.0.

The BSD-3-Clause license requires retaining copyright notices and
disclaiming warranties; the GPL-3.0 packages (`bioio-czi`, `bioio-lif`,
`aicspylibczi`) additionally require that the license text and
corresponding source be made available on distribution. Since exact
versions are pinned in [requirements.txt](requirements.txt), the
corresponding source for every package is the matching tag on PyPI/GitHub
at that version. See each project's LICENSE file at the links above, and
the [GPL-3.0 text](../LICENSE) at the root of this repository.
