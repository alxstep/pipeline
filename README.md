# Jenkins Pipeline Shared Library Sample

This project provides easy example of shared library which can be used into Jenkins pipeline.

Setup instructions

1. In Jenkins, go to Manage Jenkins → Configure System. Under Global Pipeline Libraries, add a library with the following settings:
  * Default version: Specify a Git reference (branch or commit SHA), e.g. master
  * Retrieval method: Modern SCM
  * Select the Git type
  * Project repository: https://github.com/AndreyVMarkelov/jenkins-pipeline-shared-lib-sample.git
  * Credentials: (leave blank)

2. Then create a Jenkins job with the following pipeline (note that the underscore _ is not a typo):

```
@Library('jenkins-pipeline-shared-lib-sample')_

stage('Print Build Info') {
    printBuildinfo {
        name = "Sample Name"
    }
} stage('Disable balancer') {
    disableBalancerUtils()
} stage('Deploy') {
    deploy()
} stage('Enable balancer') {
    enableBalancerUtils()
} stage('Check Status') {
    checkStatus()
}
```

Run job!