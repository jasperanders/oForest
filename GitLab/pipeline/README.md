# Pipeline Project

This project contains the pipeline configuration. The `gitlab-ci.yaml` gets referenced by all other experiment projects like so:

```yaml
include: 'https://gitlab.com/oforest/pipeline/raw/.gitlab-ci.yaml'
```
