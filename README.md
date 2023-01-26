# Docker Homework

### Task 1

1. Install docker
2. Prepare a dockerfile based on Apache or Nginx image
3. Added your own index.html page with your name and surname to the docker image
4. Run the docker container at port 8080
5. Open page in Web Browser
6. Report save in GitHub repository

To accomplish this task, I've brought up a virtual machine on AWS with ubuntu 20.04.
In the next step I installed docker on virtual machine. To do this, I used the following commands:

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
~~~
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
~~~

2. Add Docker’s official GPG key:
~~~
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
~~~

3. Set up the repository:
~~~
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
~~~

4. Update the apt package index:
~~~
sudo apt-get update
~~~

5. Install Docker Engine, containerd, and Docker Compose.
~~~
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
~~~
![Successfully install Docker](install-docker.png)

To test the success of the Docker installation, I ran the command 
~~~
sudo docker run hello-world
~~~
![Run HELLO WORLD](run-helloworld.png)

In order to use Docker without sudo, I ran the following commands:
1. Create the docker group.
~~~
sudo groupadd docker
~~~

2. Add your user to the docker group.
~~~
sudo usermod -aG docker $USER
~~~
And then I restarted a virtual machine.

After that I created folder in which created 2 files index.html and Dockerfile. In index.html file I added simple html code with my name and surname. In Dockerfile I added instructions with adding index.html file to nginx image.

Then I ran the following command to build my own image with name myfile and version latest:
~~~
docker build -t myfile:latest
~~~

To run my image I ran the following command:
~~~
docker run -d -p 8080:80 myfile:latest
~~~

After run this command I went to browser and wrote next address 3.72.0.41:8080. The page with my name and surname opened in the tab.

![My name](name.png)

The index.html and [Dockerfile files are available at the following link]().