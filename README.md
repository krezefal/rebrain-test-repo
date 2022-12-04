# The Coolest Project

[![License](https://img.shields.io/bower/l/t?label=License)](https://gitlab.rebrainme.com/devops_users_repos/4556/rebrain-devops-task1/-/blob/master/README.md)
[![Last Release](https://img.shields.io/bower/v/t?color=red&label=Latest)](https://gitlab.rebrainme.com/devops_users_repos/4556/rebrain-devops-task1/-/releases)
[![Coverage](https://img.shields.io/azure-devops/coverage/swellaby/opensource/25?label=Coverage)](https://gitlab.rebrainme.com/devops_users_repos/4556/rebrain-devops-task1/)

**Repository for The Coolest Project**

## Description
Imagine that this project is a client-server cli (_command line interface_) application specially developed for the Coolest Startup, that allows users to perform their tasks using remote resources, namely using virtual machines. This app uses the `oVirt` API since the storage allocates new resources using `oVirt` virtualisation.

This tool has been developed to automate users' access to remote capacities without disturbing the Devops specialist. Also exploiting this tool by the user **guarantees the safety and consistency of both each virtual machine and the entire oVirt system deployed on the storage**. Using this tool user can perform the following things:
- Authorizing in remote system and get access to personal pool of VMs by a unique token;
- Leasing new VMs by specifying:
    - Linux distro (available: `RedHat`, `Debian`, `Fedora`, `CentOS`)
    - Memory (from 512MB to 4GB included)
    - Storage space (from 10GB to 30GB included)
    - CPU (from 1 to 4 included)
    - Leasing time (**max leasing time = 1 month**)
- Deleting its own VMs (therefore freeing up the storage resources);
- Using VMs until their expiration date;
- Viewing his VMs list.

This Coolest tool may be compiled as a stand-alone binary using `Golang`.

> It supports some specification version [infinity+1](https://www.critterbabies.com/animals/cats-kittens/).

<!-- The link above references to photos with kittens  -->

## Table of Contents

* [Maintainer Guide](https://thecoolestproject/maintainer_guide)
* [Committer Guide](https://thecoolestproject/committer_guide)
* [Contributing Guide](https://thecoolestproject/contributing_guide)
* [Installation](#installation)
* [Building](#building)
* [Configuration](#configuration)
* [Using Tool](#using-tool)
* [Support](#support)
* [Security](https://thecoolestproject/security/SECURITY.md)
* [Documentation](#documentation)
* [Authors](#authors)

## Installation

You can install this tool using most Linux package managers, such as `dpkg`, `yum`, `dnf`, `pacman`. For example (Fedora):

```
sudo dnf install cool-tool
```

But you can also install it by cloning this repo and build the binary manually (see the section **Builbing** below):

```
git clone git@gitlab.rebrainme.com:devops_users_repos/4556/rebrain-devops-task1.git
```


## Building
This project is a Go module (see golang.org Module information for explanation).
The dependencies for this project are listed in the go.mod file.

To build the source, execute `make clean build`.

To run unit tests, execute `make test`.

To build an image, execute `make docker`.

## Configuration

To set the configuration under your environment follow the detail [configuration setup]().

## Using Tool

Firstly, to get access to `oVirt` through the `cool-tool` you just need to get token from those who has admin rights and authorize:

```
$cool-tool connect
```

Then you need to insert your token to the terminal (token will not be displayed).
> Authorization (access to the tool, not to VMs) ends for 10 minutes of inactivity

To lease new VM you need to execute

```
$cool-tool lease --name <new-vm-1> --distro <distro> --memory <amount of memory> --storage <amount of storage> --cpu <cpu capacity> --time <leasing time>
```

> Arguments `name` and `time` are optional. Default name for VM is *new-vm-<#>* and default leasing time is **_1 day_**.

To view a list of your VMs, execute

```
$cool-tool list
```

> Maximum amount of VMs = 5

You can use `--verbose` flag to get more detailed output, e.g.:

|   VM ID  | IP                |       OS      |  CPU  | Memory | Storage | Expiration date
|:--------:|:-----------------:|:-------------:|:-----:|:------:|:-------:|:--------------:
| db3c1097 | 192.168.64.128/24 |   CentOS 7    |   4   |  4 GB  |  30 GB  |   2022-12-15
| 36f39e3a | 192.168.64.134/24 |   Fedora 35   |   4   |  3 GB  |  10 GB  |   2022-12-15
| f120caa2 | 192.168.64.135/24 |   Debian 12   |   4   |  2 GB  |  20 GB  |   2022-12-20

To remove a VM that has not expired yet, run

```
$cool-tool remove <vm-id>
```

> Be carefully, the command above frees the resources and erases all data that belonged to your VM

Finally, you can connect to one of your VM via ssh. 

## Support

For any The Coolest Tool issues, questions or feedback, please follow our [support process]().

## Documentation
For more detailed information on the tool and user cases, please refer to [The Coolest Project documentation](https://www.critterbabies.com/animals/puppies/).

<!-- The link above references to photos with puppies  -->

## Authors

All this shit was generated by me (Github link):

<table>
<tr>
  <td align="center"><a href="https://github.com/krezefal"><img src="https://avatars.githubusercontent.com/u/64612172?v=4" width="100px;" alt=""/><br /><sub><b>Timofey Klimov</b></sub></a></td>
</tr>
</table>

What I did?

- [x] I do my best
- [x] I knew smth new about Markdown
- [x] Inserted links to photos with kittens 