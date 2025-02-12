A parent pipeline is a pipeline that triggers a downstream pipeline in the same project. The downstream pipeline is called a child pipeline.

Child pipelines:

- Run under the same project, ref, and commit SHA as the parent pipeline.
- Do not directly affect the overall status of the ref the pipeline runs against. For example, if a pipeline fails for the main branch, it’s common to say that “main is broken”. The status of child pipelines only affects the status of the ref if the child pipeline is triggered with [`strategy:depend`](https://docs.gitlab.com/ee/ci/yaml/index.html#triggerstrategy).
- Are automatically canceled if the pipeline is configured with [`interruptible`](https://docs.gitlab.com/ee/ci/yaml/index.html#interruptible) when a new pipeline is created for the same ref.
- Are not displayed in the project’s pipeline list. You can only view child pipelines on their parent pipeline’s details page