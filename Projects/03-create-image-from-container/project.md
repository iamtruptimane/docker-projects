# How to Create a Docker Image From a Container ?  
## Step1. Create a Base Container :
```bash  
docker create --name nginx_base -p 80:80 nginx:alpine
```  
Here we have requested a new container named nginx_base with port 80 exposed to localhost. We are using nginx:alpine as a base image for the container.  
## Step 2: Inspect Images :  
```bash  
docker images
``` 
If you look at the list of images on your system, you will now see the nginx:alpine image.  
##  
Step 3: Inspect Containers :  
```bash  
docker ps -a
```
Note here that the container is not running, so you won’t see it in the container list unless you use the -a flag (-a is for all).  
##  Step 4: Start the Container : 
 ```bash 
 docker start nginx_base
```  
Now visit http://localhost with your browser. You will see the default “Welcome to nginx!” page. We are now running an nginx container.

## Step 5: Create an Image From a Container :  

we want to know how to save this container as an image so we can make other containers based on this one. The Docker commands to do this :  
```bash  
docker commit nginx_base 
```  
Now look at the docker images list:
```bash  
docker images -a
```  
You can see there is a new image there. It does not have a repository or tag, but it exists. This is an image created from the running container. Let’s tag it so it will be easier to find later.  
## Step 6: Tag the Image :  
Using docker tag, we can name the image we just created. We need the image ID for the command.  
```bash  
docker tag <image_ID> <new_image_name>
```  
And if we look at the index of images again, we can see that the <None>s were replaced.  
## Step 7: Create Images With Tags :  
 You can also tag the image as it is created by adding another argument to the end of the command like this:  
 ```bash  
 docker commit nginx_base <new_image_name>
 ```  
 This command effectively commits and tags at the same time, which is helpful but not required.