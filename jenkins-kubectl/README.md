# Jenkins image with kubectl support

Custom image of Jenkins with addtional kubectl package.
You can use it to submit kubernetes manifest to your cluster with Kubernetes Plugin.

You can pull the image from: 
> docker pull umeshkumhar/jenkins-kubectl:latest


# Build instructions
1. git clone https://github.com/umeshkumhar/custom-docker-images.git
2. cd custom-docker-images/jenkins-kubectl
3. docker build -t imagename:tag .
4. docker images

