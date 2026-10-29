# Bruno Backstage sample

Sample collections for trying the Bruno plugin in a local Backstage app. Nothing here is a real API.

Repository: https://github.com/devsi-bruno/bruno-backstage-sample

## What is in here

| Path | Use it for |
| --- | --- |
| `collections/Notes API` | OpenCollection. The folder contains `opencollection.yml`. The space in the name checks `%20` URLs. |
| `collections/tasks-api` | Bruno collection. The folder contains `bruno.json`. |
| `collections/no-manifest` | A folder with no manifest. The wizard should report that no yml file was found. |
| `collections` | The parent folder. It also has no manifest, so it should show the same error. |
| `catalog/bruno.yaml` | Catalog file. Paste its blob URL into `catalog.locations`. |

There is no `catalog-info.yaml` at the repository root. The Create Pull Request flow adds that file.

## Wizard

Backstage must be running with `GITHUB_TOKEN` set, and you must be signed in with GitHub before creating a pull request.

OpenCollection (found):

```
https://github.com/devsi-bruno/bruno-backstage-sample/tree/main/collections/Notes%20API
```

bruno.json (found):

```
https://github.com/devsi-bruno/bruno-backstage-sample/tree/main/collections/tasks-api
```

No manifest (error, Next stays disabled):

```
https://github.com/devsi-bruno/bruno-backstage-sample/tree/main/collections/no-manifest
```

## Catalog file in app-config

Add this under `catalog.locations`, then restart the backend. The target ends at the catalog file.

```yaml
- type: url
  target: https://github.com/devsi-bruno/bruno-backstage-sample/blob/main/catalog/bruno.yaml
  rules:
    - allow: [Bruno]
```

`sample-notes-api` and `sample-tasks-api` should appear. They come from the file, so they have no Edit or Delete buttons.

`partOf` on the Notes entity points at `api:default/github-rest-api`, which the demo catalog already includes.

## Add the entity in the UI

Use either collection folder URL, choose **Add Entity directly to catalog**, and pick an entity name that is not already in the catalog (`sample-notes-api` and `sample-tasks-api` are taken once the catalog file above is loaded). That entity is stored in this Backstage instance and shows Edit and Delete.
