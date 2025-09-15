```
kubectl get hpa -n aspose
kubectl describe hpa viewgrid -n aspose
kubectl get pods -n aspose
kubectl get pods -n aspose -l app=viewgrid -w


kubectl -n aspose run -i --tty load-generator --image=busybox /bin/sh
while true; do wget -q -O- http://<your-service-name>; done


kubectl get hpa viewgrid -n aspose -w
kubectl get pods -n aspose -l app=viewgrid -w
```
