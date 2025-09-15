```
kubectl get hpa -n ns
kubectl describe hpa vg -n ns
kubectl get pods -n ns
kubectl get pods -n ns -l app=vg -w


kubectl -n ns run -i --tty load-generator --image=busybox /bin/sh
while true; do wget -q -O- http://<your-service-name>; done


kubectl get hpa vg -n ns -w
kubectl get pods -n ns -l app=vg -w

kubectl top pods
kubectl top nodes
```



```
apt update
apt install vim curl
apt install gnupg software-properties-common
curl -s https://dl.k6.io/key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/k6-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
apt update
apt install k6
```
