# Setting Up a Private Docker Registry on Debian

## 1. Install Docker

Ensure Docker is installed on your Debian server. If not, follow these steps:

```bash
sudo apt-get update
sudo apt-get install docker.io
```
# Start Docker:
```bash
sudo systemctl start docker
sudo systemctl enable docker
```
## 2. Run the Docker Registry Container:
```bash
docker run -d -p 5000:5000 --name registry registry:2
```
## 3.  Configure Docker to Use the Private Registry
```bash
sudo nano /etc/docker/daemon.jso
```
```bash
{
  "insecure-registries" : ["your-server-ip:5000"]
}
```
# Retart Docker:
```bash
sudo systemctl restart docker
```
## 4.  Push and Pull Images to/from Your Registry
```bash
docker tag your-image:tag your-server-ip:5000/your-image:tag
```
```bash
docker push your-server-ip:5000/your-image:tag
```
```bash
docker pull your-server-ip:5000/your-image:tag

```
