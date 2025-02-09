# create-advisory-internal-request

Tekton task to create an advisory via an InternalRequest. The advisory data is pulled from the data JSON. The origin workspace from
the ReleasePlanAdmission and Application from the Snapshot are also used. The advisory is created in a GitLab repository.

## Parameters

| Name                     | Description                                                                               | Optional | Default value               |
|--------------------------|-------------------------------------------------------------------------------------------|----------|-----------------------------|
| jsonKey                  | The json key containing the advisory data                                                 | Yes      | .advisory                   |
| releasePlanAdmissionPath | Path to the JSON file of the ReleasePlanAdmission in the data workspace                   | Yes      | release_plan_admission.json |
| snapshotPath             | Path to the JSON file of the Snapshot spec in the data workspace                          | Yes      | snapshot_spec.json          |
| dataPath                 | Path to data JSON in the data workspace                                                   | Yes      | data.json                   |
| request                  | Type of request to be created                                                             | Yes      | create-advisory             |
| synchronously            | Whether the task should wait for InternalRequests to complete                             | Yes      | true                        |
| pipelineRunUid           | The uid of the current pipelineRun. Used as a label value when creating internal requests | No       |                             |

## Changes in 1.0.0
- The internalrequest CR is created with a label specifying the pipelinerun uid with the new pipelineRunUid parameter
  - This change comes with a bump in the image used for the task

## Changes since 0.1.0
- Updated hacbs-release/release-utils image to reference redhat-appstudio/release-service-utils image instead
