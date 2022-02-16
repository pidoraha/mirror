# mirror
mirror chart to expose input data

# Getting started:
helmfile:
```
environments:
  dev:
    values:
      - environments/dev.yaml
      - environments/dev-migration.yaml
  prod:
    values:
      - environments/prod.yaml
      - environments/prod-migration.yaml
---

helmfiles:
  - path: git::ssh://git@github.com:pidoraha/mirror.git@helmfile.yaml?ref=master
  #- path: git::ssh://git@<mygit>/<myrepo>/<mypath>/charts-<mychart>.git@deploy/helmfile.yaml?ref=master
    selectorsInherited: true
    values:
      {{- toYaml (list .Environment.Values) | nindent 6 }}
      - app_name: elements

```
