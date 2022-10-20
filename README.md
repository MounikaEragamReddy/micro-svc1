CI:
Docker Build
aws ecr login | docker login
docker build -t ecrRepoUrl:tag
docker push ecrrepourl:tag

CD:
kubectl apply -f *
 