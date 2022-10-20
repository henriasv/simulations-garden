---
{"dg-publish":true,"permalink":"/dee-pmd/running-a-docker-image-containing-deepmd/","dgHomeLink":true,"dgPassFrontmatter":false}
---


This command runs a docker image with deepmd-kit, and both exposes and navigates to the current working directory on the host machine. 
```bash
docker run -t -i -v $PWD:$PWD -w $PWD --gpus all ghcr.io/deepmodeling/deepmd-kit:2.1.4_cuda11.6_gpu
```
The Nvidia Container toolkit must be installed for this to work. 

To add a user for allowing to run docker images (havent checked security implications of this)
```
sudo usermod -a -G docker <username>
```
