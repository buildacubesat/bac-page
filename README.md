# bac.page

Short URL forwarding service for [Build a CubeSat](https://buildacubesat.space) – an open-source electronics project for accessible space hardware.

Slugs resolve via static HTML redirects hosted on GitHub Pages. Like everything in the BAC project, this tool is fully open source.

## Usage

The CLI lives in [bac-utils](https://github.com/buildacubesat/bac-utils) as `tools/bac-page` since its 0.5.0; install it from that checkout and point it at your local clone:

    uv tool install ./tools/bac-page
    bac-page --init

Create a short URL with an auto-generated slug:

    bac-page https://docs.buildacubesat.space/some/long/path
    # → https://bac.page/aB3x9kLm

Or specify your own (1–24 characters: letters, digits, and hyphens):

    bac-page https://docs.buildacubesat.space/some/long/path eps-v2r1
    # → https://bac.page/eps-v2r1

The CLI creates the redirect file, commits, and pushes in one step. The short URL is live within ~30 seconds once GitHub Pages deploys.

`bac-page list` shows all redirects, `bac-page edit` changes a slug or destination, and `--qr` generates a QR code. See [its README](https://github.com/buildacubesat/bac-utils/tree/main/tools/bac-page) for all options.

## Repo structure

    <slug>/            One folder per short URL, each containing an index.html redirect
    index.html         Landing page served at bac.page/
    404.html           Shown for unknown slugs
    CNAME              GitHub Pages custom domain config

## License

[MIT](LICENSE)
