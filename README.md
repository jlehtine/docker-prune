# Docker resource pruning tool

A simple shell script for pruning the selected Docker resources in one go.

Docker based development often leaves a lot of resources around in the
development environment. I found myself often using the various pruning
commands of the "docker" utility and wrapped up the most commonly used
sequences into a single script.


## Usage

Let the tool speak for itself...

```
$ ./docker-prune -h
Removes unused Docker resources. By default removes only the dandling images.

To remove the stopped containers and their volumes as well as unused volumes
and networks use "-s" (stopped). To stop the running containers and then remove
resources associated with all containers, use "-a" (all).

To remove all unused images including tagged ones, use "-t" (tagged).

To remove everything, use "-e" (everything), implying -a -t.

See other options below.

usage: docker-prune [-a] [-t] [-q] [-f]
       docker-prune [-s] [-t] [-q] [-f]
       docker-prune [-e] [-q] [-f]
       docker-prune -h

options:
    -h    print this help text and exit without doing anything else
    -s    remove resources associated with the stopped containers
    -a    remove resources associated with all containers
    -t    remove tagged images that are not used by any containers
    -e    remove everything
    -q    be quiet, suppress informative output
    -f    force it, omit all confirmation dialogs
```

## Example

```
$ ./docker-prune -s -t
Will remove the stopped containers:
- container2
- ubuntuexperiment
- demo-db

Will remove their volumes and any unused volumes

Will remove tagged images not used by any container

Are you sure you want to proceed? (y/N): y

Removing unused containers...
Removed 3 unused containers
Total reclaimed space: 10.72GB

Removing unused networks...

Removing unused volumes...
Removed 2 unused volumes
Total reclaimed space: 1.427GB

Removing unused images...
Removed 17 unused images
Total reclaimed space: 1.047GB
```


## License

Copyright (c) 2021 Johannes Lehtinen

Licensed under the MIT License, see "LICENSE"
