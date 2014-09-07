# CloudStack Simulator Dockerfile

This Dockerfile creates Docker Image that contains CloudStack simualtor and 
some utilities.

## Usage

### Use from Vagrant

* Start simulator

```sh
# vagrant up --provider docker
```

* Stop simulator

```sh
# vagrant halt
```

* Reset simulator

```sh
# vagrant reload
```

* Destroy simulator

```sh
# vagrant destroy
```

## Notes

This project is inspired by a following project.

* https://github.com/bvbharatk/VagrantSimulator
  * Install CloudStack simulator and datacenter. Most of Dockerfile commands are derived from this project.
