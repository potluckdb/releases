# potluckdb releases

potluckdb is local-first SQLite synchronized through plain object storage,
with no server. Start with the [documentation](https://docs.potluckdb.com).

This repository is the GitHub channel of every potluckdb release: the
binaries, their checksums, and the evidence that they work. The primary
download host is `https://downloads.potluckdb.com/releases`, which each
release's manifest pins as its `download_base_url`; the bytes here are the
same bytes, published a second time somewhere a release can be fetched
with nothing but a browser.

No source is here, and none will be. potluckdb is a commercial product
built in a private repository — see the [license notice](LICENSE) and the
documentation for licensing.

## What a release carries

- the Universal C SDK archives for every platform;
- the language-SDK packages (wheels, npm tarballs, crates, NuGet, Maven,
  pub.dev archives);
- the WASM runtimes for browser and Node;
- `release-manifest.json`, naming every one of those packages, and
  `SHA256SUMS`;
- the validation report, the changelog, the performance measurements and
  the artefact sizes, so the evidence outlives the run that produced it
  and can be re-checked without a login;
- `promotion.json`.

## Verifying a download

`SHA256SUMS` covers the packages and `release-manifest.json`. From the
directory you downloaded into:

```sh
sha256sum --check SHA256SUMS
```

A download that passes is exactly the file every check in the release
notes ran against. The reports attached beside the packages are not in
`SHA256SUMS`; their digests are in `promotion.json`.

## `promotion.json`

The provenance record, written by the workflow that created this release
and by nothing else. It names the version, the pre-release candidate it
was promoted from, the source revision that candidate was built at, the
digests of the manifest and of `SHA256SUMS`, the download host, the number
and total size of the published files, and a digest for each of the
evidence files `SHA256SUMS` does not cover. It is the one record that ties
what is published here to what was built and tested.

## Reporting a problem

Open an issue on this repository. For anything undisclosed, do not — see
[SECURITY.md](SECURITY.md).
