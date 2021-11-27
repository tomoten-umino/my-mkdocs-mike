# Portable Gluster

This repository contains the tool to create the docker image of Glusterfs container with 2 replicas.

![Concept](./images/DevelopmentAndDeployment.en.png)

## Table of contents

- [Dependancy](#dependency)
- [Usage](#usage)
  - [Directory-Structure](#directory-structure)
  - [Setting](#setting)
  - [Building](#building)
  - [Deployment](#deployment)
- [License](#license)

## Dependency

- This tool uses the following software.
  - docker and docker-compose
  - bash
  - envsubst

## Usage

### Directory-Structure

![Directory](./images/DirectoryStructure.en.png)

### Setting

- This tool can change the following parameter names by defining them in the setup/.env file.
  - NETWORK_ADDR : Network address of the production environment.
  - HOSTNAME_1 : Gluster-container-1's name
  - IP_ADDR_1 : Gluster-container-1's address
  - HOSTNAME_2 : Gluster-container-2's name
  - IP_ADDR_2  : Gluster-container-2's address
  - VOLUME_NAME : Gluster volume name

### Building

- After moving to the setup directory, run build.sh as follows.
  - You can check the Usage by running the -h(or --help) option to build.sh
  - `AAAAA:BBBBB` is docker image name and tag.
- After executing build.sh, the docker image (portable-gluster.tar) and docker-compose.yml for deployment will be generated in the deploy directory.

```command
cd [setup directory]
./build.sh -t AAAAAA:BBBBBB   
```

### Deployment

- Transfer what is under the deploy directory to any directory in the production environment.
- After moving to the setup directory, load the docker image in the deploy directory.
  - Run as a user who can use the docker command.
- After loading docker iamge, Start the docker container as follows.
  - Run on two servers at the same time.
  - Glusterfs logs are output to the log directory.

```command
$ cd [deploy directory]
$ docker image load -i portable-gluster.tar
-- in the server 1 ----------------------------------
$ docker-compose up -d gluster-server-1
-- in the server 2 ----------------------------------
$ docker-compose up -d gluster-server-2
```

### Remarks

- The Gluster container moves the Glusterfs configuration directory in the container to the specified location at startup as the following figure.

![ConfigDir](./images/MoveConfigDirectory.en.png)

## License

This tool is released under the WTFPL, see LICENSE.
