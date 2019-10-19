---
title: Docker Connector API Reference 
keywords: sample
sidebar: docker_connector_sidebar
permalink: dc_api_reference.html
folder: docker_connector
---
# Overview

Docker Connector, built using Docker Java API client, is a communication
tool that provides seamless integration with the Docker engine from a
mule flow. It exposes Docker operations by executing their API calls as
per configuration. It supports HTTP and HTTPS connections and can be
used as inbound as well as outbound connector from the mule flow.  

**Additional Info**

| **Field**                            | **Description** |
| ------------------------------------ | --------------- |
| **Requires Mule Enterprise License** | No              |
| **Requires Entitlement**             | No              |
| **Mule Version**                     | 3.8.5           |

# Configs

## HTTP Docker Config

`<docker:HTTP-Docker-Config>`  
`Configuration`

### Attributes

| **Name**       | **Java Type** | **Description**                                                         | **Default Value** | **Required** |
| -------------- | ------------- | ----------------------------------------------------------------------- | ----------------- | ------------ |
| name           | String        | The name of this configuration. With this name can be later referenced. |                   | x            |
| dockerHostIP   | String        | Docker host IP or DNS name                                              |                   | x            |
| dockerHostPort | String        | Docker Engine Port                                                      |                   | x            |
| apiVersion     | String        | Docker Engine API version                                               | 1.24              |              |

## HTTPS Docker Config

`<docker:HTTPS-Docker-Config>`  
`Configuration`

### Attributes

| **Name**                       | **Java Type** | **Description**                                                                                          | **Default Value** | **Required** |
| ------------------------------ | ------------- | -------------------------------------------------------------------------------------------------------- | ----------------- | ------------ |
| name                           | String        | The name of this configuration. With this name can be later referenced.                                  |                   | x            |
| dockerHostIP                   | String        | Docker host IP or DNS name                                                                               |                   | x            |
| dockerHostPort                 | String        | Docker Engine Port                                                                                       |                   | x            |
| apiVersion                     | String        | Docker Engine API version                                                                                | 1.24              |              |
| clientCertificateDirectoryPath | String        | Path of directory containing certificates required for docker TLS connection (ca.pem, cert.pem, key.pem) |                   | x            |

# Processors

## Docker Info

`<docker:docker-info>`  
Get the docker information.  

**XML
Sample**  

``` xml
<docker:docker-info config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" />
```

### Attributes

| **Name**   | **Java Type** | **Description**             | **Default Value** | **Required** |
| ---------- | ------------- | --------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use |                   | x            |

### Returns

| **Return Java Type** | **Description**                                                 |
| -------------------- | --------------------------------------------------------------- |
| Info                 | Docker info like number of containers, number of images, server |

## List Containers

`<docker:list-containers>`  
Get the list of containers.

**XML
Sample**  

``` xml
<docker:list-containers config-ref="Docker__HTTP_Docker_Config"    doc:name="Docker"/>
```

### Attributes

| **Name**   | **Java Type** | **Description**                                                      | **Default Value** | **Required** |
| ---------- | ------------- | -------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use                                          |                   | x            |
| showAll    | boolean       | Show all container: Running and Exited                               | false             |              |
| before     | String        | Show only containers created before Id, include non-running ones     |                   |              |
| limit      | int           | Show limit last created containers, include non-running ones         | 0                 |              |
| showSize   | boolean       | Show the containers sizes                                            | false             |              |
| status     | String        | Container status like created,restarting,running,paused,exited,dead. | running           |              |
| labels     | String        | labels associated with the container                                 |                   |              |

### Returns

| **Return Java Type** | **Description**                    |
| -------------------- | ---------------------------------- |
| List                 | Listing of all running containers. |

## Create Container

`<docker:create-container>`  
Create a container on docker host using a docker image.

**XML
Sample**  

``` xml
<docker:create-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="ubuntuContainer" imageName="ubuntu" jsonFilePath="src\main\resources\CreateContainer.json"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                                                                                                          | **Default Value** | **Required** |
| ------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------ | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                                                                                              |                   | x            |
| imageName     | String        | Docker image name to be used to create the container                                                                     |                   |              |
| imageTag      | String        | Docker image tag                                                                                                         | latest            |              |
| containerName | String        | Name of the container that will be created                                                                               |                   |              |
| jsonFilePath  | String        | Path of JSON file that will be used to set request parameters. All options except Healthcheck are supported in the JSON. |                   |              |

### Returns

| **Return Java Type**    | **Description**                                 |
| ----------------------- | ----------------------------------------------- |
| CreateContainerResponse | Low-level information of the created container. |

## Inspect Container

`<docker:inspect-container>`  
Inspect the container.  

**XML
Sample**  

``` xml
<docker:inspect-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test" showSize="true"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                   | **Default Value** | **Required** |
| ------------- | ------------- | --------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use       |                   | x            |
| containerName | String        | Name of the existing container    |                   | x            |
| showSize      | boolean       | Return container size information | false             |              |

### Returns

| **Return Java Type**    | **Description**                                 |
| ----------------------- | ----------------------------------------------- |
| CreateContainerResponse | Low-level information of the created container. |

## Start Container

`<docker:start-container>`  
Start a container on docker host.  

**XML
Sample**  

``` xml
<docker:start-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test_container"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                                                                | **Default Value** | **Required** |
| ------------- | ------------- | ------------------------------------------------------------------------------ | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                                                    |                   | x            |
| containerName | String        | Name of the container to be started (container is initially in stopped state). |                   | x            |

## Stop Container

`<docker:stop-container>`  
Stop the running container.  

**XML
Sample**  

``` xml
<docker:stop-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test" timeout="10"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                                                                    | **Default Value** | **Required** |
| ------------- | ------------- | ---------------------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                                                        |                   | x            |
| containerName | String        | Name or ID of the container to be stopped (Container is initially in start state). |                   | x            |
| timeout       | int           | Number of seconds to wait before killing the container                             | 0                 |              |

## Restart Container

`<docker:restart-container>`  
Restart the container.  

**XML
Sample**  

``` xml
<docker:restart-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test" timeout="10"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                                        | **Default Value** | **Required** |
| ------------- | ------------- | ------------------------------------------------------ | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                            |                   | x            |
| containerName | String        | Name or ID of the running container                    |                   | x            |
| timeout       | int           | Number of seconds to wait before killing the container | 0                 |              |

## Kill Container

`<docker:kill-container>`  
Kill the container.  

**XML
Sample**  

``` xml
<docker:kill-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test" signal="SIGKILL"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                                                                                                                                | **Default Value** | **Required** |
| ------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                                                                                                                    |                   | x            |
| containerName | String        | Name or ID of the running container                                                                                                            |                   | x            |
| signal        | String        | Signal to send to the container: integer or string like SIGINT. When not set, SIGKILL is assumed and the call waits for the container to exit. | SIGKILL           |              |

## Pause Container

`<docker:pause-container>`  
Pause the container.  

**XML
Sample**  

``` xml
<docker:pause-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test_container"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                     | **Default Value** | **Required** |
| ------------- | ------------- | ----------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use         |                   | x            |
| containerName | String        | Name or ID of the running container |                   | x            |

## Unpause Container

`<docker:unpause-container>`  
Unpause the container.  

**XML
Sample**  

``` xml
<docker:unpause-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test_container"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                     | **Default Value** | **Required** |
| ------------- | ------------- | ----------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use         |                   | x            |
| containerName | String        | Name or ID of the running container |                   | x            |

## Wait for A Container

`<docker:wait-a-container>`  
Wait for a container with given name or ID to execute.  

**XML
Sample**  

``` xml
<docker:wait-a-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test_container" />
```

### Attributes

| **Name**      | **Java Type** | **Description**                                | **Default Value** | **Required** |
| ------------- | ------------- | ---------------------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                    |                   | x            |
| containerName | String        | Name or ID of the container that needs to wait |                   | x            |

## Delete Container

`<docker:delete-container>`  
Delete the container with container name or ID.  

**XML
Sample**  

``` xml
<docker:delete-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test" forceDelete="true" removeVolumes="true"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                                  | **Default Value** | **Required** |
| ------------- | ------------- | ------------------------------------------------ | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                      |                   | x            |
| containerName | String        | Name or ID of the container                      |                   | x            |
| forceDelete   | boolean       | Force remove container                           | false             |              |
| removeVolumes | boolean       | Remove the volumes associated with the container | false             |              |

## Run Container

`<docker:run-container>`  
A custom operation where Create-Container and Start-Container operations
are performed.  

**XML
Sample**  

``` xml
<docker:run-container config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" containerName="test" imageName="ubuntu"/>
```

### Attributes

| **Name**      | **Java Type**  | **Description**                                | **Default Value** | **Required** |
| ------------- | -------------- | ---------------------------------------------- | ----------------- | ------------ |
| config-ref    | String         | Specify which config to use                    |                   | x            |
| imageName     | String         | Docker image name used to create the container |                   | x            |
| imageTag      | String         | Docker image tag                               | latest            |              |
| containerName | String         | Container name or ID which will be created     |                   | x            |
| command       | List\<String\> | Command executed while running container       |                   |              |

### Returns

| **Return Java Type**    | **Description**                                                |
| ----------------------- | -------------------------------------------------------------- |
| CreateContainerResponse | Low level details of the container gets generated from docker. |

## List Images

`<docker:list-image>`  
Get the list of images.  

**XML
Sample**  

``` xml
<docker:list-image config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" dangling="true" imageNameFilter="ubuntu" showAll="true"/>
```

### Attributes

| **Name**         | **Java Type** | **Description**                        | **Default Value** | **Required** |
| ---------------- | ------------- | -------------------------------------- | ----------------- | ------------ |
| config-ref       | String        | Specify which config to use            |                   | x            |
| showAll          | boolean       | Display all the images                 | false             |              |
| dangling         | boolean       | Images with dangling status            | false             |              |
| imageNameFilter  | String        | Return images with the specified name  |                   |              |
| imageLabelFilter | String        | Return images with the specified label |                   |              |

### Returns

| **Return Java Type** | **Description**        |
| -------------------- | ---------------------- |
| List                 | Listing of all images. |

## Build an image from Docker file

`<docker:build-image>`  
Create an image using docker file.  

**XML
Sample**  

``` xml
<docker:build-image config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" dockerFilePath="src\main\resources\Dockerfile"/>
```

### Attributes

| **Name**          | **Java Type**        | **Description**                                                                   | **Default Value** | **Required** |
| ----------------- | -------------------- | --------------------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref        | String               | Specify which config to use                                                       |                   | x            |
| dockerFilePath    | String               | Path of the Docker file                                                           |                   | x            |
| imageTags         | List\<String\>       | Tag to apply to the image in the "name:tag" format                                |                   | x            |
| cpuSet            | String               | CPUs in which to allow execution (e.g., 0-3, 0,1)                                 |                   |              |
| cpuShares         | String               | CPU shares (relative weight)                                                      |                   |              |
| labels            | Map\<String,String\> | Key-value labels to set on the image                                              |                   |              |
| memory            | long                 | Memory limit for build (in Bytes)                                                 | 0                 |              |
| memswap           | long                 | Total memory (memory + swap). Set as -1 to disable swap                           | \-1               |              |
| buildArgumetName  | String               | Name of build-time variables                                                      | null              |              |
| buildArgumetValue | String               | Value of build-time variables                                                     |                   |              |
| cacheFromImage    | List\<String\>       | Use the cache when building the image                                             |                   |              |
| noCache           | Boolean              | Do not use the cache when building the image                                      | false             |              |
| forcerm           | Boolean              | Always remove intermediate containers, even upon failure                          | true              |              |
| pullImage         | Boolean              | Attempt to pull the image even if an older image exists locally.                  | true              |              |
| removeContainers  | Boolean              | Remove intermediate containers after a successful build                           |                   | x            |
| remoteURI         | String               | A Git repository URI or HTTP/HTTPS context URI pointing to Dockerfile or tarball. |                   |              |

### Returns

| **Return Java Type** | **Description**                     |
| -------------------- | ----------------------------------- |
| InspectImageResponse | Low-level information of the image. |

## Pull Image

`<docker:pull-image>`  
Pull an image from docker registry to the docker host.  

**XML
Sample**  

``` xml
<docker:pull-image config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" imageName="ubuntu"/>
```

### Attributes

| **Name**   | **Java Type** | **Description**                                                                 | **Default Value** | **Required** |
| ---------- | ------------- | ------------------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use                                                     |                   | x            |
| imageName  | String        | Docker image name or the registry url for the image like localhost:5000/ubuntu. |                   | x            |
| imageTag   | String        | Docker image tag                                                                | latest            |              |
| username   | String        | Username for the private registry                                               |                   |              |
| password   | String        | Password for the private registry                                               |                   |              |

### Returns

| **Return Java Type** | **Description**                               |
| -------------------- | --------------------------------------------- |
| InspectImageResponse | Low-level information on the image imageName. |

## Inspect Image

`<docker:inspect-image>`  
Inspect an image to get the low level information of the image.  

**XML
Sample**  

``` xml
<docker:inspect-image config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" imageName="ubuntu"/>
```

### Attributes

| **Name**   | **Java Type** | **Description**              | **Default Value** | **Required** |
| ---------- | ------------- | ---------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use  |                   | x            |
| imageName  | String        | Docker image name to inspect |                   | x            |
| imageTag   | String        | Docker image tag             | latest            |              |

### Returns

| **Return Java Type** | **Description**                               |
| -------------------- | --------------------------------------------- |
| InspectImageResponse | Low-level information on the image imageName. |

## Push Image

`<docker:push-image>`  
Push an image to registry.  

**XML
Sample**  

``` xml
<docker:push-image config-ref="Docker__HTTP_Docker_Config1" doc:name="Docker"   imageName="test_image" imageTag="test_image_tag" />
```

### Attributes

| **Name**   | **Java Type** | **Description**                                                                 | **Default Value** | **Required** |
| ---------- | ------------- | ------------------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use                                                     |                   | x            |
| imageName  | String        | Docker image name or the registry url for the image like localhost:5000/ubuntu. |                   | x            |
| imageTag   | String        | Tag of the image that is to be pushed to registry                               |                   |              |
| username   | String        | Username for the private registry                                               |                   |              |
| password   | String        | Password for the private registry                                               |                   |              |

### Returns

| **Return Java Type** | **Description**                               |
| -------------------- | --------------------------------------------- |
| InspectImageResponse | Low-level information on the image imageName. |

## Tag Image

`<docker:tag-image>`  
Tag a docker image.  

**XML
Sample**  

``` xml
<docker:tag-image config-ref="Docker__HTTP_Docker_Config1" doc:name="Docker" destImageName="dest_image_name" destImagetag="dest_tag" imageName="test_image" imageTag="test_image_tag" repository="localhost:5000"/>
```

### Attributes

| **Name**      | **Java Type** | **Description**                               | **Default Value** | **Required** |
| ------------- | ------------- | --------------------------------------------- | ----------------- | ------------ |
| config-ref    | String        | Specify which config to use                   |                   | x            |
| imageName     | String        | Name of the source image                      |                   | x            |
| imageTag      | String        | Tag of the source image                       |                   |              |
| destImageName | String        | Name of the image to be reflected in registry |                   | x            |
| repository    | String        | Repository URL                                |                   | x            |
| destImagetag  | String        | Tag of the image in registry                  |                   | x            |

## Remove Image

`<docker:remove-image>`  
Delete the image with given image name or ID.  

**XML
Sample**  

``` xml
<docker:remove-image config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" forceRemove="true" imageName="ubuntu" prune="true"/>
```

### Attributes

| **Name**    | **Java Type** | **Description**                            | **Default Value** | **Required** |
| ----------- | ------------- | ------------------------------------------ | ----------------- | ------------ |
| config-ref  | String        | Specify which config to use                |                   | x            |
| imageName   | String        | Docker image name that needs to be removed |                   | x            |
| imageTag    | String        | Docker image tag                           |                   |              |
| forceRemove | Boolean       | Force remove image                         | false             |              |
| prune       | boolean       | Do not delete untagged parent images       | false             |              |

## List Volumes

`<docker:list-volume>`  
List the volumes.  

**XML
Sample**  

``` xml
<docker:list-volume config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" danglingFilter="true"/>
```

### Attributes

| **Name**       | **Java Type** | **Description**                                                    | **Default Value** | **Required** |
| -------------- | ------------- | ------------------------------------------------------------------ | ----------------- | ------------ |
| config-ref     | String        | Specify which config to use                                        |                   | x            |
| danglingFilter | boolean       | Returns all volumes that are dangling (not in use by a container). | false             |              |

### Returns

| **Return Java Type** | **Description**          |
| -------------------- | ------------------------ |
| ListVolumesResponse  | Listing volume response. |

## Create Volume

`<docker:create-volume>`  
Create new volume on docker.  

**XML
Sample**  

``` xml
<docker:create-volume config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" volumeDriver="custom" volumeName="tardis"/>
```

### Attributes

| **Name**     | **Java Type**        | **Description**                                                                                                  | **Default Value** | **Required** |
| ------------ | -------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------- | ------------ |
| config-ref   | String               | Specify which config to use                                                                                      |                   | x            |
| volumeName   | String               | The new volume’s name                                                                                            |                   | x            |
| volumeDriver | String               | Name of the volume driver to use                                                                                 | local             |              |
| driverOpts   | Map\<String,String\> | A mapping of driver options and values. These options are passed directly to the driver and are driver specific. |                   |              |

### Returns

| **Return Java Type** | **Description**                           |
| -------------------- | ----------------------------------------- |
| CreateVolumeResponse | The low level info of the created volume. |

## Inspect Volume

`<docker:inspect-volume>`  
Inspect volume for low-level information on the given volume name.  

**XML
Sample**  

``` xml
<docker:inspect-volume config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" volumeName="tardis"/>
```

### Attributes

| **Name**   | **Java Type** | **Description**             | **Default Value** | **Required** |
| ---------- | ------------- | --------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use |                   | x            |
| volumeName | String        | Volume name or ID           |                   | x            |

### Returns

| **Return Java Type**  | **Description**                                 |
| --------------------- | ----------------------------------------------- |
| InspectVolumeResponse | Low-level information on the given volume name. |

## Remove Volume

`<docker:remove-volume>`  
Operation to remove a volume.  

**XML
Sample**  

``` xml
<docker:remove-volume config-ref="Docker__HTTP_Docker_Config"  doc:name="Docker" volumeName="tardis"/>
```

### Attributes

| **Name**   | **Java Type** | **Description**             | **Default Value** | **Required** |
| ---------- | ------------- | --------------------------- | ----------------- | ------------ |
| config-ref | String        | Specify which config to use |                   | x            |
| volumeName | String        | Volume name or ID           |                   | x            |

# Sources

## Get container logs

`<docker:get-container-logs>`  
Get logs from the container with given container name or container ID.  

**XML
Sample**  

``` xml
<docker:get-container-logs config-ref="Docker__HTTP_Docker_Config" containerName="test" showTimeStamp="true" followStream="true" standardOut="true" standardError="true" doc:name="Docker (Streaming)"/>
```

### Attributes

| **Name**       | **Java Type**                                                                                             | **Description**                                             | **Default Value** | **Required** |
| -------------- | --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ----------------- | ------------ |
| config-ref     | String                                                                                                    | Specify which config to use                                 |                   | x            |
| sourceCallback | SourceCallback parameter to process the callback which represents the next message processor in the chain |                                                             |                   | x            |
| containerName  | String                                                                                                    | Name or ID of the running container                         |                   | x            |
| showTimeStamp  | boolean                                                                                                   | Select to show time stamp with log statement                | false             |              |
| standardOut    | boolean                                                                                                   | Print timestamps for every log line. Show standard out logs | false             |              |
| standardError  | boolean                                                                                                   | Show standard error logs                                    | false             |              |
| showSince      | int                                                                                                       | Show logs since timestamp or relative Minutes               | 10                |              |
| tail           | int                                                                                                       | Output specified number of lines at the end of logs         | 0                 |              |
| followStream   | boolean                                                                                                   | Follow the logs                                             | false             |              |

### Returns

| **Return Java Type** | **Description** |
| -------------------- | --------------- |
| void                 |                 |

## Get container statistics

`<docker:get-container-statistics>`  
Get information of a container’s resource usage statistics.  

**XML
Sample**  

``` xml
<docker:get-container-statistics config-ref="Docker__HTTP_Docker_Config" containerName="test" doc:name="Docker (Streaming)"/>
```

### Attributes

| **Name**       | **Java Type**                                                                                             | **Description**                     | **Default Value** | **Required** |
| -------------- | --------------------------------------------------------------------------------------------------------- | ----------------------------------- | ----------------- | ------------ |
| config-ref     | String                                                                                                    | Specify which config to use         |                   | x            |
| sourceCallback | SourceCallback parameter to process the callback which represents the next message processor in the chain |                                     |                   | x            |
| containerName  | String                                                                                                    | Name or ID of the running container |                   | x            |

### Returns

| **Return Java Type** | **Description** |
| -------------------- | --------------- |
| void                 |                 |


{% include links.html %}
