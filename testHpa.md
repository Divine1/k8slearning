```
kubectl get hpa -n ns
kubectl describe hpa vg -n ns
kubectl get pods -n ns
kubectl get pods -n ns -l app=vg -w


kubectl -n ns run -i --tty load-generator --image=busybox /bin/sh
while true; do wget -q -O- http://<your-service-name>; done


kubectl get hpa vg -n ns -w
kubectl get pods -n ns -l app=vg -w
```
