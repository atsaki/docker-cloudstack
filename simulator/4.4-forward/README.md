# CloudStack Simulator Dockerfile

This Dockerfile creates Docker Image that contains CloudStack simualtor and 
some utilities.

## Usage

### Use from Vagrant

1. Install Vagrant and Git if they are not installed

2. Pull Docker Image

  ```sh
  docker pull atsaki/cloudstack-simulator-4.4
  ```

3. Clone this repository

  ```sh
  git clone https://github.com/atsaki/docker-cloudstack.git
  cd docker-cloudstack/simulator/4.4-forward
  ```

4. Download insecure key

  ```sh
  curl -o insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
  chmod 600 insecure_key
  ```

5. Start container

  ```sh
  vagrant up --provider docker
  ```

6. Wait a few minutes until management server get started

  You can tail log with following command.

  ```sh
  vagrant ssh -c tail -f /var/log/cloudstack_simulator.log
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
