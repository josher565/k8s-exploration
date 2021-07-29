# Kaniko image build 

I'm experimenting here with building from a dockerfile from a container in k8s. The result of the build is pushed into my docker repository. 
After, I can pull the image and see a result by running the resulting container by attaching a console.

## Create pod, volume & volume claim files

### SSH into the kube
`kubectl ssh`

Just the above ssh's into the kube. Then we create a minimal docker file that pulls a ubuntu image and echos "hello world". 2 lines. It lives in /home/docker/kaniko

### Create a secret for docker registry for my account

`kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=notauser --docker-password=notasecret --docker-email=user@example.com`

secret/regcred created

### Create Objects
```bash
PS C:\src\kaniko> kubectl create -f volume.yaml
persistentvolume/dockerfile created

PS C:\src\kaniko> kubectl create -f volume-claim.yaml
persistentvolumeclaim/dockerfile-claim created

Pod.yaml
Change the destination to a docker hub repository.
I had to create the repository in docker hub.

PS C:\src\kaniko> kubectl create -f pod.yaml
pod/kaniko created
```

## Sources
* https://github.com/GoogleContainerTools/kaniko/blob/master/docs/tutorial.md