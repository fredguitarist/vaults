[[gitlab]]

A downstream pipeline is any GitLab CI/CD pipeline triggered by another pipeline. Downstream pipelines run independently and concurrently to the upstream pipeline that triggered them.

- A [[Parent-child pipelines]] is a downstream pipeline triggered in the _same_ project as the first pipeline.
- A [[Multi-project pipelines]] is a downstream pipeline triggered in a _different_ project than the first pipeline.

You can sometimes use parent-child pipelines and multi-project pipelines for similar purposes, but there are [key differences](https://docs.gitlab.com/ee/ci/pipelines/pipeline_architectures.html).