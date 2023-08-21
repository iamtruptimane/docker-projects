## Steps to add a user to the docker group :  
### Step 1. Create a docker group :  
You can skip this step if docker group already exists. You can check using :  
```bash 
grep docker /etc/group   
```  
To create a new group named docker, type:
```bash
sudo groupadd docker
```  
If the command execution is successful then it exists without output.  

### Step 2. Add user to the docker group :
```bash
sudo usermod -aG docker $USER
```  
The usermod command with -a option means that you are adding or appending the user to a particular group. This should always be used with the -G option which specifies the group that the user is currently in. $USER indicates that we are going to add the currently logged-in non-root user. For a not-logged-in user, you have to explicitly mention the username.  
### Step 3. Make the changes effective :  
```bash
sudo systemctl restart docker
```  
  
Note: In case you running a virtual machine it's necessary to restart it.  

### Step 4. Verify : 
 Now let us run the docker command to verify that you can run as a non-root user. Let us run the hello-world docker. 



```bash 
docker run hello-world 
```  
# conclusion :  

 We end up with this solution because of the fact that the root user owns the socket and non-users can only access using sudo.

This got solved by adding the user to the docker group, so when docker starts socket is accessible to its members. Moreover, remember docker group grants root privilege to the user.
