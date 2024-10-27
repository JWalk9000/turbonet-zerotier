## This Is A Work In Progress and a Learning Experience: ```fully working at this time```

Can be used as a starting base for other images to include Zerotier functionality.

# ZeroTier One Docker Image 
 
 This repository contains the necessary files to build and run a ZeroTier One image using both Podman and Docker. The setup includes a Containerfile and a podman-compose.yml file (rename to ```Dockerfile``` &```docker-compose.yml``` if using Docker and Docker-Compose. 
 
 ## Getting Started  
 
 ### Overview 
 
 1. Clone the Repository: Fetch the files from GitHub. 
 2. Build the Image: Create the Docker/Podman image. 
 3. Configuration: Adjust settings for your environment. 
 4. Running the Container: Start your ZeroTier container. 
 
 ### Prerequisites 
 
 Ensure you have the following installed on your system: 
 - Docker or Podman
 - docker-compose or podman-compose respecfully
 - curl 
 - git (for cloning this repository) 
 
 ## 1. Clone the Repository 
 
 From in your target directory, clone the repository from GitHub and optionally set your own folder name: 
 ```sh 
 git clone https://github.com/jwalk9000/turbonet-zerotier.git [your-folder-name] 
 cd [your-folder-name] 
 ```
 
 ## 2. Build the Image 
 
 Navigate to the directory containing the build file: Containerfile for podman, rename to Dockerfile for Docker: 
 ```sh 
 cd /path/to/Buildfile 
 ```
 
 ### Using Docker 
 
 Build the Docker image: 
 ```sh 
 docker build -t myzerotierimage . 
 ```
 
 ### Using Podman 
 
 Build the Podman image: 
 ```sh 
 podman build -t myzerotierimage . 
 ```

 Change ```myzerotierimage``` to any name you choose, remember to change the image name in the compose.yml to match.
 
 ## 3. Configuration 

 ### Network ID
 Set your ZeroTier Network ID in the compose.yml file: 
 ```sh
 environment: 
 - ZEROTIER_NETWORK_ID=<YOUR_NETWORK_ID> 
 ```
Replace ```<YOUR_NETWORK_ID>``` with your actual ZeroTier Network ID. 

### Persistant Data
Set the local machine director in the compose.yml file:
```sh
volumes:
 - /home/podman/zerotier/data:/var/lib/zerotier-one
```
Replace ```/home/podman/zerotier/``` with where you want persistant data to be saved.

 
 ## 4. Running the Container 
 
 
 ### Using Podman 
 
 Run the Podman container with podman-compose: 
 ```sh 
 podman-compose up -d 
 ```

### Using Docker 
 
 Run the Docker container with docker-compose: 
 ```sh 
 docker-compose up -d 
 ```
 
 
 ## Notes 
 
 - The Containerfile installs the necessary packages, and sets up ZeroTier One. 
 - The podman-compose.yml file maps the necessary devices and ports, ensures the container joins your specified ZeroTier network, and that your configuration data is persisted. 
 
 ## Troubleshooting 
 
 If you encounter any issues: 
 
 1. Check the container logs: 
 ```sh 
 docker logs myzerotiercontainer 
 ```
 or 
 ```sh 
 podman logs myzerotiercontainer 
 ```
 
 2. Ensure that your network configurations allow ZeroTier traffic. 
 
 ## Contributing 
 
 Feel free to submit pull requests or report issues to improve this setup. 
 
 ## License 
 
 This project is licensed under the MIT License.
