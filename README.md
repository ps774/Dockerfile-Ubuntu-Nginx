# Dockerfile-Ubuntu-Nginx
# Dockerfile-Image
#In a jenkins job, we can Build-image and Run-container using Publish over SSH plugin
#These are the commands we have to run in Exec commond block

cd ~/MyDocker
docker image prune -a -f
docker build -t ngximg:${BUILD_NUMBER} .
docker rm -f ngxweb
docker run -dit -p 8082:80 --name ngxweb ngximg:${BUILD_NUMBER}
