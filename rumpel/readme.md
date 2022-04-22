# rumpel-mock 

**early version, trying things out!**


helm install < name-of-service-being-faked > rumpel/ --set-file rumpelContract=< path to contract.json >

eg: helm install locationservice rumpel/ --set-file rumpelContract=contract.json

