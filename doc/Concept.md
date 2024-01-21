# Concept

This is a comparison document regarding `minikube`, `kind`, `k3d` and containing their summary, basic characteristics, pros and cons.

In the end of the document, there are demo and conclusion regarding the best choice.

## Intro

`minikube`, `kind`, and `k3d` are tools for deploying Kubernetes clusters in a local environment.

### minikube

`minikube` is a tool that lets you run Kubernetes locally. It runs a single-node Kubernetes cluster inside a VM on your laptop for users looking to try out Kubernetes or develop with it day-to-day.
It supports various Kubernetes features like DNS, NodePorts, ConfigMaps and Secrets, making it a good option for developers looking to replicate a full-fledged Kubernetes environment on their local machine.
`minikube` offers an easy-to-setup and relatively resource-friendly way to learn and experiment with Kubernetes.

### kind

`kind` (Kubernetes in Docker) is a tool for running local Kubernetes clusters using Docker container “nodes”.
`kind` was primarily designed for testing Kubernetes itself, but may be used for local development or CI.
It uses Docker to create a cluster of containerized "nodes", with one container representing a single node in the cluster.
`kind` is especially useful for CI/CD pipelines, as it allows for rapid deployment and teardown of clusters.

### k3d

`k3d` is a lightweight wrapper around `k3s`, a certified Kubernetes distribution designed for production workloads in unattended, resource-constrained, remote locations or inside IoT appliances.
The main purpose of `k3d` is to run a `k3s` cluster in Docker containers. It's particularly useful for local development and testing, as it allows for easily creating, deleting, and managing Kubernetes clusters on a personal computer.
`k3d` is known for its simplicity and ease of use, making it a popular choice for developers who need a quick and easy way to run Kubernetes locally.

## Characteristics

| |minikube|kind|k3d|
|-|--------|----|---|
|supported OS|Windows, macOS, Linux|compatibility same to the the Docker|compatibility same to the the Docker|
|supported architectures|AMD64, ARM|compatibility same to the the Docker|compatibility same to the the Docker|
|automation|through configuration files and CLI|through configuration files|through configuration files|
|additional features|supports Podman|supports Podman|supports Podman|

## Pros and cons

| |minikube|kind|k3d|
|-|--------|----|---|
|pros|convenient for beginners, rich functionality; strong community support|lightweight, fast, good isolation, CI/CD support; widely-used|lightweight, fast, additional Helm support; gaining popularity|
|cons|large resource consumption, potential issues with VM stability|may be less stable compared to a real Kubernetes cluster|may be less stable for large projects|

## Demo

k3d + test container

![k3d + test container](./assets/concept/demo.gif)

## Conclusion

Considering the nature and structure of the startup, I would use `k3d` as a lightweight Docker-based tool that would be great for both quick local development and production. In case of Docker licensing risks, this tool also supports Podman.
