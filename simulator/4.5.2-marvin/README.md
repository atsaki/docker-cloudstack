# CloudStack Simulator Dockerfile

This Dockerfile creates Docker Image that contains CloudStack simualtor

## Usage

2. Pull Docker Image

  ```sh
  docker pull atsaki/cloudstack-simulator
  ```

3. Run the contanier

  ```sh
  docker run --name cloudstack -d -p 8080:8080 atsaki/cloudstack-simulator
  ```

## Acknowledgement

This image is based on [cloudstack/simulator](https://hub.docker.com/r/cloudstack/simulator/).

