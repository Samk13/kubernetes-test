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

Solution 4:
[Using group access permissions](http://blog.dscpl.com.au/2015/12/random-user-ids-when-running-docker.html)

Solution 5:
[create a new docker group and add the user to the docker group](https://github.com/rhtconsulting/rhc-ose/blob/7afca118f1f883200d5867bfc11785d1dcba1440/docker/openstack-client-rhel/README.md)