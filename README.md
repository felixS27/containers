# containers

Recipes and images for containers used in Nextflow modules and pipelines.
Images are published on [GHCR](https://github.com/felixS27?tab=packages).

## Containers

| Name | Description | Version | Image |
|---|---|---|---|
| [bioio](bioio/) | Bioimage file I/O (CZI, LIF, ND2, OME-TIFF, OME-Zarr, ...) via [bioio](https://github.com/bioio-devs/bioio) | 3.5.0 | `ghcr.io/felixs27/bioio:3.5.0` |
| [deconwolf](deconwolf/) | GPU-accelerated deconvolution of widefield fluorescence microscopy images via [deconwolf](https://github.com/elgw/deconwolf) | 0.4.6 | `ghcr.io/felixs27/deconwolf:0.4.6` |

## Usage

Reference an image in a Nextflow module's `container` directive, e.g.:

```groovy
process {
    withName: 'BIOIO_.*' {
        container = 'ghcr.io/felixs27/bioio:3.5.0'
    }
}
```

## Structure

Each container lives in its own subfolder with:

- `Dockerfile` — the build recipe
- `NOTICE.md` — third-party licenses and, where relevant, citation info for the packaged software

To add a new container, create a subfolder following this convention, then build and push to GHCR:

```sh
docker build -t ghcr.io/felixs27/<name>:<version> <name>/
docker push ghcr.io/felixs27/<name>:<version>
```

## License

This repository's own code is licensed under the terms in [LICENSE](LICENSE).
Each container may package third-party software under different licenses — see that container's `NOTICE.md` for details.
