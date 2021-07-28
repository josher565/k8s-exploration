# Start a Basic Busybox image
The point being that busybox is a nice command line in the cluster. Good for debugging latest resources

## Start up minikube
1. open powershell as admin
2. minikube start
3. WAIT for it
4. run command as follows

    ```bash
    kubectl run -i --tty --rm debug --image=busybox --restart=Never -- sh
    ```

## Sources:  
* https://raw.githubusercontent.com/kubernetes/kubernetes/master/hack/testdata/recursive/pod/pod/busybox.yaml
* https://medium.com/@pczarkowski/kubernetes-tip-run-an-interactive-pod-d701766a12
