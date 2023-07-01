# Kubernetes-Challenge 1:

1. First create the pvc using definition file:

```bash
kubectl apply -f pvc-definition.yml
```

2. Next create pod using defin file:

```bash
kubectl apply -f pod-definition.yml
```
3. Next the svc, make sure to use correct labels:

```bash
kubectl apply -f svc-definition.yml
```
4. kubectl create role developer-role --resource=pods,svc,pvc --verb="*" -n development
5. kubectl create rolebinding developer-rolebinding --role=developer-role --user=martin -n development
6. kubectl config set-credentials martin --client-certificate ./martin.crt --client-key ./martin.key
7. kubectl config set-context developer --cluster kubernetes --user martin
8. kubectl config use-context developer