# p-portfolio
This is a personal portfolio website created using html, css and Js.

I will be showing you how to create a dockerfile, build,verify and test docker image, create a dockerhub repo, push docker image to docker hub and finally, pull and run the image from docker hub.

Step 1: Create dockerfile in the root directory of the project


![image](https://github.com/user-attachments/assets/acca3ae7-5d74-414c-b0da-584554c813cc)


add the following content to the dockerfile created;
# Use an official nginx image as the base image
FROM nginx:alpine
# Copy the HTML files to the nginx html directory
COPY . /usr/share/nginx/html
# Expose port 80
EXPOSE 80
# Start nginx when the container starts
CMD ["nginx", "-g", "daemon off;"]


 Step 2: Build docker image using the below command -- in your gitbash terminal
 docker build -t website:latest . 

 This command tells Docker to build an image from the Dockerfile in the current directory (denoted by .) and tag it as website with the latest tag. You should see something like this...


 
![image](https://github.com/user-attachments/assets/32da4469-a966-4f62-b963-61fa4ac5c0e1)


step 3: verify the docker image using the command (docker images). Your image should be listed among the other images


![image](https://github.com/user-attachments/assets/c0f87b85-c9ee-4b92-82cd-5e28f7ab6622)


step 4: Build and deploy the container with the image we created earlier using the command:
$ docker run -d -p 8080:80 website:latest


![image](https://github.com/user-attachments/assets/078dca70-f1dd-4922-8844-8fb9daabab70)


In my case, i received an error "port not available" because my port 8080 was being used by jenkins. Hence, i changed my port to 8050


![image](https://github.com/user-attachments/assets/b4ff11f4-e5e9-4c27-a6e4-a9898bbbb3ee)


This command runs the Docker container in detached mode (-d), maps port 8050 on your host to port 80 in the container (-p 8050:80), and uses the website image.
Open your web browser and navigate to http://localhost:8050. You should see your simple website running.


![image](https://github.com/user-attachments/assets/735fdb18-e7da-44ed-b259-3dde1deb7092)


step 5: Tag the docker image

$ docker tag website:latest zkyusya/website:latest
step 6: Login in to the dockerhub from the command line using command (docker login)


![image](https://github.com/user-attachments/assets/77cabbeb-5543-4749-8064-6da08a501a41)


step 7: Push the docker image to Docker Hub

$ docker push zkyusya/website:latest


![image](https://github.com/user-attachments/assets/b77da5c7-6313-4ed3-9a0d-a3dcd5797186)


Go to Docker Hub in your web browser.
Navigate to your profile and find the website repository.
Verify that the image is listed under the “Tags” section.
Step 8: Pull and Run the Image from Docker Hub
To verify that your image works when pulled from Docker Hub, you can run it on any machine with Docker installed:
$ docker run -d -p 8050:80 zkyusya/website:latest

LETS WRAP IT ALL WITH THIS SIMPLE DOCKER CLI CHEATSHEET....



![image](https://github.com/user-attachments/assets/beda3d3c-3e11-41eb-b7c2-971403fe3d92)
![image](https://github.com/user-attachments/assets/35cbb9d5-8033-411d-a509-0628a371e4a1)
![image](https://github.com/user-attachments/assets/2eced9e3-81d5-40f7-8c2a-1452568bc7a1)
![image](https://github.com/user-attachments/assets/cd0d1edf-120a-4400-91f6-cd4c5956d6da)

What next??...check out my next tutorial on using Docker Compose to manage multi-container Docker applications, automating the building, running, and linking multiple services like web servers, databases, and caching services.
Ciao!










 

