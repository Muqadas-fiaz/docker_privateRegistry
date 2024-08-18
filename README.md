# Setting Up a Private Docker Registry on Debian

## 1. Install Docker

Ensure Docker is installed on your Debian server. If not, follow these steps:

```bash
sudo apt-get update
sudo apt-get install docker.io

Start Docker

bash

sudo systemctl start docker
sudo systemctl enable docker

2. Run the Docker Registry Container

Run the Docker registry using the official registry image:

bash

docker run -d -p 5000:5000 --name registry registry:2

3. Configure Docker to Use the Private Registry

To configure Docker to trust your private registry, create or edit the Docker daemon configuration file:

bash

sudo nano /etc/docker/daemon.json

Add the following JSON configuration:

json

{
  "insecure-registries" : ["your-server-ip:5000"]
}

Replace your-server-ip with the IP address or domain of your server.
Restart Docker

bash

sudo systemctl restart docker

4. Push and Pull Images to/from Your Registry
Tag the Image

bash

docker tag your-image:tag your-server-ip:5000/your-image:tag

Push the Image

bash

docker push your-server-ip:5000/your-image:tag

Pull the Image

bash

docker pull your-server-ip:5000/your-image:tag
