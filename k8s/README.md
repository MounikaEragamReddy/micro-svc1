CI:
DockerBuild:
        aws ecr login | docker login
        docker build -t ecrRepoUrl:tag
        docker push ecrRepoUrl:tag
CD:
kubectl apply -f deployment.yaml service.yaml ingress.yaml namespace.yaml
