# files-context-financial-services

A Meltano [file bundle](https://docs.meltano.com/concepts/plugins/#file-bundles) of **industry
context for financial services**. Meltano Cloud adds it to a workspace whose organisation's industry
is Financial Services.

The bundle holds datasets with no query. Each one is a written briefing: the segments and source
systems of the industry, its core entities, the metrics it runs on, how to model its data in dbt,
and how to handle its data. They are written for an AI assistant (or an analyst) working in the
workspace, for example one building dbt models on raw financial data.

```
analyze/datasets/financial-services/
  overview.yml
  data-model.yml
  metrics.yml
  dbt-modelling.yml
  data-handling.yml
```

## Install

Meltano Cloud installs it when Financial Services is chosen as the workspace's industry, in the
setup wizard or with the `set_organisation_context` MCP tool.

In a Meltano project of your own:

```yaml
# meltano.yml
plugins:
  files:
    - name: files-context-financial-services
      variant: matatika
      pip_url: git+https://github.com/meltano/files-context-financial-services.git@v0.1.0
      update:
        '*.yml': true
```

```sh
meltano install files files-context-financial-services
```

`update: '*.yml': true` lets `meltano upgrade files` refresh the datasets from a newer version.

## Release

Tag a version (`git tag -a v0.1.1 -m v0.1.1 && git push --tags`) and bump the `pip_url` ref in the
Meltano Cloud registry definition (`plugins/files/files-context-financial-services--matatika.yml`).

These datasets are general industry context, not legal, regulatory or financial advice.
