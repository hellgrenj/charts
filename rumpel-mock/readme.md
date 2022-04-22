# rumpel-mock 

**early version, trying things out!**


## tldr install
``helm repo add hellgrenj https://hellgrenj.github.io/charts/``  
``helm repo update``  
``helm install my-mock hellgrenj/rumpel-mock --set-file rumpelContract=contract.json``

## install and test 
1.  run ``helm repo add hellgrenj https://hellgrenj.github.io/charts/`` 
2. run ``helm repo update`` 
3. to test this out create a contract.json file with the following content:

 ```
 {
  "Name": "consumer-api",
  "URL": "http://api:1337",
  "Transactions": [
    {
      "Request": {
        "Path": "/scakes",
        "Method": "GET",
        "RawBody": "",
        "Headers": {
          "Accept": [
            "*/*"
          ],
          "User-Agent": [
            "Deno/1.20.6"
          ],
          "Accept-Encoding": [
            "gzip, br"
          ]
        }
      },
      "Response": {
        "StatusCode": 200,
        "Headers": {
          "Date": [
            "Tue, 19 Apr 2022 18:22:15 GMT"
          ]
        },
        "RawBody": "[{\"id\":1,\"name\":\"SecureCake\",\"ingredients\":\"secure things\"}]"
      },
      "Customizations": [],
      "SimulatedConditions": []
    }
  ]
}
``` 
4. In the same directory run: ``helm install my-mock hellgrenj/rumpel-mock --set-file rumpelContract=contract.json``
5. run ``kubectl get pods`` to see the pod running
6. port-forward to the running pod, eg: ``kubectl port-forward <name-of-pod> 8181:8181``
7. navigate to http://localhost:8181/scakes and see the response from your rumpel-mock

(check logs with ``kubectl logs <name-of-pod>``)
