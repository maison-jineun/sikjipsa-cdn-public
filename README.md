# sikjipsa-cdn-public

Serving tree for the sikjipsa mini app. Every file here is generated and pushed by the deploy tool of the private repository. Edits made here are overwritten by the next deploy.

## Branches

| Branch | Environment |
|---|---|
| `develop` | staging |
| `main` | production |

Each commit message ends with `(private <sha>)`, the source commit it was built from.

## URLs

Files are served through jsDelivr by branch:

```
https://cdn.jsdelivr.net/gh/maison-jineun/sikjipsa-cdn-public@<branch>/<path>
```

The app reads `api/v1/domain/index.json` first. Its `dataVersion` is a content hash of the whole tree, and the app fetches the rest only when that value changes.

```
api/v1/domain/index.json                 summary of all species, page counts, dataVersion
api/v1/domain/species/<key>.json         one species
api/v1/domain/tips/pages/<n>.json        tips, oldest page first
api/v1/domain/notice/pages/<n>.json      notices, oldest page first
static/content/…                         HTML pages opened inside the app
```
