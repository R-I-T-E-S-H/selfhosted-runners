# Building the container
docker build -t github-runner .

# Register a runner to a repository for Docker
docker run --name github-runner \
     -e GITHUB_OWNER=username-or-organization \
     -e GITHUB_REPOSITORY=my-repository \
     -e GITHUB_PAT=[PAT] \
     github-runner

# Kubernetes Deployment
kubectl create secret generic githubpat --from-literal=pat=[PAT] -n [namespace]
kubectl apply -f deployment.yaml -n [namespace]