# Jenkins.Pipeline.buildimage

Jenkinsfile for docker image building as airflow jobs (using capitalone's model).

[Copyrighted (C)2023 Dwight Spencer. All Rights Reserved.](/LICENCE.md)


## Requirements

Name|Version|Description
-|-|-
Jenkins|2.414+|CICD system
Docker|1.13+|Build environment
Docker Hub|API KEY|Creditential added to Jenkins


## Installation

Follow the steps in the [official documentation from jenkins/cloudbees](https://www.jenkins.io/doc/tutorials/using-jenkinsfile-runner-github-action-to-build-jenkins-pipeline/)

# FAQ

## What's with the name?

Jenkins, Airflow, etc. are the new COBOL/JCL/MVS world. So in honor of the old mainframe mindset.
We're using the common DD dataset style instead of the reverse domain style of UUCP/USENET/Java
that is more common in modern programming paradimes and used for the past decade in my own projects.


### What does this do?

Setups a pipeline for Jenkins that uses buildpack for creating python containers (or arbutrary images)
so Airflow DAGs using the `DockerOperator()` can execute them. Thus elminating dependancy hell from Airflow,
and making the system ready for migration to Tekton, Portainer, or Nomad when the need arises.
