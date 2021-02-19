#build Image 

docker build -t "bhojrajp/coffeweb" .

#Run docker container image

docker run -p  5000:80 bhojrajp/coffeweb

#browse 
http://localhost:5000

#-d - run the container in detached mode (in the background)
#-p 80:80 - map port 80 of the host to port 80 in the container
#docker/getting-started - the image to use