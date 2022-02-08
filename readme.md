To run kubectl:

follow the [instructions](https://minikube.sigs.k8s.io/docs/start/)


fix permisson denied in open shift when you try to run .sh file

solution 1:
```bash
oc adm policy add-scc-to-user anyuid -z default -z default
```
Be aware that this is a security risk. and recommended best practice is to avoid containers that need to run as root.

Solution 2:
```bash
chmod +x file.sh

Solution 3:
You can get around the problem by adding --privileged to the docker run call, e.g.

docker run --privileged --name oc-cluster-up ...