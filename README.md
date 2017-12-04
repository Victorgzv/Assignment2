# Assignment2
A DockerCMS.
To run this application run the bash script named a2.sh

https://www.youtube.com/watch?v=QKVt7N_XpYg&feature=youtu.be


#Get all containers
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/containers | python -mjson.tool

#Get all running containers
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/containers?state=running | python -mjson.tool

#Get all services 
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/services | python -mjson.tool

#Get all nodes
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/nodes | python -mjson.tool

#Delete container by ID
curl -s -X DELETE -H 'Accept: application/json' http://35.189.108.29:5000/containers/72fd74d32a91

#Get container by ID
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/containers/d3da335c8e27 | python -mjson.tool

#Get an specific container logs
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/containers/d3da335c8e27/logs | python -mjson.tool

#Get all images
curl -s -X GET -H 'Accept: application/json' http://35.189.108.29:5000/images | python -mjson.tool

#Change state of container to running
curl -X PATCH -H 'Content-Type: application/json' http://35.189.108.29:5000/containers/301407c69d21 -d '{"state": "running"}'  

#Change state of container to stopped
curl -X PATCH -H 'Content-Type: application/json' http://35.189.108.29:5000/containers/301407c69d21 -d '{"state": "stopped"}' 

#Create docker image
curl -H 'Accept: application/json' -F "file=@./lab5-todo-repo/Dockerfile" http://35.189.108.29:5000/images

#Change state of image
curl -s -X PATCH -H 'Content-Type: application/json' http://35.189.108.29:5000/images/747cb2d60bbe -d '{"tag": "test:1.0"}'  

#Delete Image by ID (Nginx image)
curl -s -X DELETE -H 'Accept: application/json'  http://35.189.108.29:5000/images/135342612904  

#Create a container
 curl -X POST -H 'Content-Type: application/json' http://35.189.108.29:5000/containers -d '{"image": "9e7424e5dbae"}'

#Delete all containers (must all be stopped)
curl -s -X DELETE -H 'Accept: application/json' http://35.189.108.29:5000/containers 
#Delete all images
curl -s -X DELETE -H 'Accept: application/json' http://35.189.108.29:5000/images
