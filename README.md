## Introduction

Ruby API for the [https://docs.tutum.co/reference/api/](tutum) HTTP API.  Tutum is a docker host PaaS.  See the tutum documentation for a full list of parameters for each method call.

## Authentication

```ruby
  require 'tutum'
  tutum = Tutum.new(TUTUM_USERNAME, API_KEY)
```

## Containers

### Create a new container

```ruby
  tutum.containers.create({
    :image_name => "tutum/hello-world", 
    :name => "my-awesome-app", 
    :container_size => "XS", 
    :web_public_dns => "awesome-app.example.com"
  })
```

### List all containers

```ruby
  tutum.containers.list({})
```

### Get container details

```ruby
  tutum.containers.get(CONTAINER_UUID)
```

### Start a container

```ruby
  tutum.containers.start(CONTAINER_UUID)
```

### Stop a container

```ruby
  tutum.containers.stop(CONTAINER_UUID)
```

### Get the logs of a container

```ruby
  tutum.containers.logs(CONTAINER_UUID)
```

### Redeploy a container

```ruby
  tutum.containers.redeploy(CONTAINER_UUID, {})
```

### Terminate a container

```ruby
  tutum.containers.delete(CONTAINER_UUID)
```

## Actions

### List all actions

```
  tutum.actions.list
```

### Get an action by UUID

```
  action = tutum.actions.get(ACTION_UUID)
```


## Providers

### List all providers

```
  tutum.providers.list
```

### Get a provider

```
  tutum.providers.get(PROVIDER_NAME)
```

## Regions

### List all regions

```
  tutum.regions.list
```

### Get an individual region

```
  tutum.regions.get(REGION_NAME)
```

## Availability Zones

TODO: Not implemented on tutum yet

## Node Types

### List all node types

```
  tutum.node_types.list
```

### Get an individual node type
```
  node_type = tutum.node_types.get("digitalocean/1gb")
```

## Node Clusters

### List all node clusters

```
  node_clusters = tutum.node_clusters.list
```

### Create a node cluster

```
  region = tutum.regions.get("digitalocean/lon1")
  node_type = tutum.node_types.get("digitalocean/1gb")
  number_of_nodes = 1
  node_cluster = tutum.node_cluster.create( "my_cluster", node_type, region, number_of_nodes)
```

### Get a node cluster

```
  service = tutum.node_clusters.get(NODE_CLUSTER_UUID)
```

### Deploy a node cluster

```
  tutum.node_clusters.deploy(NODE_CLUSTER_UUID)
```

### Update an existing node cluster
```
  tutum.node_clusters.update(NODE_CLUSTER_UUID, :target_num_nodes => 3)
```

### Terminate a node cluster
```
  tutum.node_clusters.delete!(NODE_CLUSTER_UUID)
```

## Nodes

### List all nodes

```
tutum.nodes.list
```

### Get an existing node

```
tutum.nodes.get(NODE_UUID)
```

### Deploy a node

```
tutum.nodes.deploy(NODE_UUID)
```

### Terminate a node

```
tutum.nodes.terminate(NODE_UUID)
```

## Services

### List all services
```
options = {}
tutum.services.list(options)
```

### Create a new service

```
service = tutum.services.create('tutum/hello-world, :name => "my-new-app", :target_num_containers => 1)
```

### Get an existing service

```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

service = tutum.services.get(service_uuid)
```

### Get the logs of a service

```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

tutum.services.logs(service_uuid)
```

### Update an existing service

```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

tutum.services.update(service_uuid, :target_num_containers => 3)
```

### Start a service

```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

tutum.services.start(service_uuid)
```

### Stop a service
```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

tutum.services.stop(service_uuid)
```


### Redeploy a service
```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

tutum.services.redeploy(service_uuid)
```

### Terminate a service
```
service_uuid = "7eaf7fff-882c-4f3d-9a8f-a22317ac00ce"

tutum.services.terminate(service_uuid)
```


### About

The ruby tutum API is provided by 255 BITS LLC.  Please star it if you like it.

### License

MIT

### Changelog

v0.1.1 Fix runtime dependency
v0.1.0 Initial release
