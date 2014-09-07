# CloudStack Simulator Dockerfile

This Dockerfile creates Docker Image that contains CloudStack simualtor and 
some utilities.

## Usage

### Use from Vagrant

1. Install Vagrant and Git if they are not installed
2. Clone this repository

```sh
git clone https://github.com/atsaki/docker-cloudstack.git
cd docker-cloudstack/simulator/4.4-forward
```

3. Download insecure key

```sh
curl -o insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
chmod 600 insecure_key
```

4. Start simulator

```sh
vagrant up --provider docker
```

#### Supported commands

* Start simulator

```sh
vagrant up --provider docker
```

* SSH login to the container

```sh
vagrant ssh
```

* Stop simulator

```sh
vagrant halt
```

* Reset simulator

```sh
vagrant reload
```

* Destroy simulator

```sh
vagrant destroy
```

## Notes

This project is inspired by a following project.

* https://github.com/bvbharatk/VagrantSimulator
  * Install CloudStack simulator and datacenter. Most of Dockerfile commands are derived from this project.
