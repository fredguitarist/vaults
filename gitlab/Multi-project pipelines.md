A pipeline in one project can trigger downstream pipelines in another project, called multi-project pipelines. The user triggering the upstream pipeline must be able to start pipelines in the downstream project, otherwise [the downstream pipeline fails to start](https://docs.gitlab.com/ee/ci/pipelines/downstream_pipelines_troubleshooting.html#trigger-job-fails-and-does-not-create-multi-project-pipeline).

Multi-project pipelines:

- Are triggered from another project’s pipeline, but the upstream (triggering) pipeline does not have much control over the downstream (triggered) pipeline. However, it can choose the ref of the downstream pipeline, and pass CI/CD variables to it.
- Affect the overall status of the ref of the project it runs in, but does not affect the status of the triggering pipeline’s ref, unless it was triggered with [`strategy:depend`](https://docs.gitlab.com/ee/ci/yaml/index.html#triggerstrategy).
- Are not automatically canceled in the downstream project when using [`interruptible`](https://docs.gitlab.com/ee/ci/yaml/index.html#interruptible) if a new pipeline runs for the same ref in the upstream pipeline. They can be automatically canceled if a new pipeline is triggered for the same ref on the downstream project.
- Are visible in the downstream project’s pipeline list.
- Are independent, so there are no nesting limits.

If you use a public project to trigger downstream pipelines in a private project, make sure there are no confidentiality problems. The upstream project’s pipelines page always displays:

- The name of the downstream project.
- The status of the pipeline.