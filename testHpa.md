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
gpg -k
gpg --no-default-keyring --keyring /usr/share/keyrings/k6-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | tee /etc/apt/sources.list.d/k6.list
apt-get update
apt-get install k6
```



```
import http from 'k6/http';
import { sleep } from 'k6';
import { check, fail } from 'k6';
import { htmlReport } from "https://raw.githubusercontent.com/benc-uk/k6-reporter/main/dist/bundle.js";

export const options = {
  vus: 1,
  iterations: 3,
  discardResponseBodies: true,
};


const ids = [5,5,5,5,5, 5,5,5,5,5, 5,5,5,5,5]
export default function () {
  // Stagger the requests by VU number
  sleep(__VU * 0.015); // 50ms delay per VU
  const documentId = documentIds[__VU - 1];

  const startTime = new Date().toISOString();
  
  const response = http.get(`https://url`, {timeout: '120s', headers: {'token': 'token'}});
  const isSuccess = check(response, {
    'status is 200': (r) => r.status === 200,
  });
  // Log failed responses
  if (!isSuccess) {
    console.log(`❌ FAILED: Status ${response.status} for URL: ${response.url}`);
    // console.log(`Response body: ${response.body}`);
    console.log(`VU: ${__VU}, ITER: ${__ITER}`);
  }
  console.log(`VU ${__VU} request sent at ${startTime}`);
}

export function handleSummary(data) {
  return {
    "summary.html": htmlReport(data),
  };
}

```
