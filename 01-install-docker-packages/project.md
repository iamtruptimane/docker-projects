## How to install docker-ce on linux?  
### Step1: Set up the repository  
```bash 
sudo yum install -y yum-utils

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

```  
### Step2:   Install Docker Engine   
```bash
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

``` 
### Step3: Start docker service  
```bash  
sudo systemctl start docker
```
## How to install docker-compose on linux?  
### Step1: Check the current release and if necessary, update it in the command below:  
```bash  
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```   
### Step2: set the permissions to make the binary executable:  
```bash  
sudo chmod +x /usr/local/bin/docker-compose
```  
### Step3:      verify that the installation was successful by checking the version:  
```bash  
docker-compose --version
```



