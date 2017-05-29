# Base Docker images for Focus community projects with JDK

This repository contains images used as a base image for *all* Focus community images that require Java Development Kit.

## Types of images

Currently this repository contains following images:

1. JDK 7 (in the `jdk7` branch)
2. JDK 8 (in the `jdk8` branch)

Both images **extend** the `focus/base:latest` image and add latest OpenJDK distribution for selected version. Additionally a `JAVA_HOME` environment variable is set.

## Availability

Both images are built on Docker HUB and available for immediate pull from the public registry.

### OpenJDK 7

    docker pull focus/jdk:7

### OpenJDK 8

    docker pull focus/jdk:8
    
## Issues

All issues should be reported in the [GitHub issue tracker](https://github.com/Focus-Dockerfiles/jdk/issues).