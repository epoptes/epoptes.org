---
title: Docker Connector Release Notes
keywords: sample
sidebar: docker_connector_sidebar
permalink: dc_release_notes.html
folder: docker_connector
---
The Anypoint Connector for Docker lets you connect to the docker engine
and docker registry. The connector exposes convenient methods for
exploiting the capabilities of Docker.

The connector executes API calls targeting Docker’s REST API depending
on you configuration. The API calls use an JSON request/response over
HTTP and HTTPS connection. All required request HTTP and HTTPS
connection configurations are abstracted and built into the connector.

Read through this user guide to understand how to set up and configure a
basic flow using the connector. Track feature additions, compatibility,
limitations, and API version updates using the Docker Connector Release
Notes. Review the connector operations and see how they work by
reviewing the Technical Reference alongside the Demo Applications.

[Docker Connector User Guide](dc_user_guide.html)

# Docker Connector V1.0.0 - February 8, 2018

## Version V1.0.0 Compatibility

| Software     | Version |
| ------------ | ------- |
| Mule Runtime | 3.8.5   |
| Docker       | 1.24    |

## Features

1.  TLS support with docker engine

2.  Supports multiple APIs of docker images, container and volumes:
    
      - Docker Info
    
      - Pull Image
    
      - Create Container
    
      - Start Container
    
      - Stop Container
    
      - Inspect Container
    
      - Run Container
    
      - Get Container Logs
    
      - Get Container Statistics
    
      - Restart Container
    
      - Kill Container
    
      - Pause Container
    
      - Unpause Container
    
      - Delete Container
    
      - List Images
    
      - Build Image from Docker File
    
      - Inspect Image
    
      - Remove Image
    
      - List Volumes
    
      - Wait for A Container
    
      - Create Volume
    
      - Inspect Volume
    
      - Remove Volume
    
      - Tag Image
    
      - Push Image

## Support Resources

  - Learn how to [Install Anypoint
    Connectors](https://docs.mulesoft.com/mule-user-guide/v/3.7/installing-connectors) using
    Anypoint Exchange.

  - Access MuleSoft’ [Forum](http://forum.mulesoft.org/mulesoft) to pose
    questions and get help from Mule’s broad community of users.

  - To access MuleSoft’s expert support team,
    [subscribe](http://www.mulesoft.com/mule-esb-subscription) to Mule
    ESB Enterprise and log in to MuleSoft’s [Customer
    Portal](http://www.mulesoft.com/support-login).

{% include links.html %}
