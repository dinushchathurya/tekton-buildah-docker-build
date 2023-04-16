### Build and Push Docker image to Docker Hub using Tekton pipeline

This is a simple sample project to demonstrate how to build and push a Docker image to Docker Hub using Tekton pipeline.

#### Used Tekton resources in this project

- git-clone task [https://hub.tekton.dev/tekton/task/git-clone]
- buildah task [https://hub.tekton.dev/tekton/task/buildah]

#### Troubleshooting

- If you get an error like this:

error while running "VolumeBinding" prebind plugin for pod "app": Failed to bind volumes: timed out waiting for the condition

You can follow the steps in the below link to fix it
[https://github.com/dinushchathurya/tekton-docker-push/blob/master/policy/README.md]   