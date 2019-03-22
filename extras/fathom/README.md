# Fathom

[Fathom](https://usefathom.com/) is a simple analytics tool, easily deployable on your local kubernetes cluster.

## Prerequisites

Persistent storage using e.g. `rook` (as described in [the guide](https://github.com/hobby-kube/guide#distributed-block-storage)) is required.

## Deployment instructions

Read the yml files carefully and replace the necessary placeholders within `secret.yml` (for `FATHOM_SECRET`) and `ingress.yml` (domain name).

After that, apply the files:

```bash
$ kubectl apply -f secret.yml
$ kubectl apply -f pvc.yml
$ kubectl apply -f deployment.yml
$ kubectl apply -f service.yml
$ kubectl apply -f ingress.yml
```

To restrict access to your `fathom` instance, add a user:

```bash
# retrieve pod name
$ kubectl get pods
$ kubectl exec -it POD_NAME -- ./fathom user add -e EMAIL -p PASSWORD
```