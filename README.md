# Installation example
You will need kubectl and helm installed
## Create your SSL certificate secret cf-tls
Create and enter folder `/tmp/deleteme`. And create empty files
```bash
mkdir /tmp/deleteme
cd /tmp/deleteme
touch cf.key
touch cf.crt
```
I have cloudflare origin certs in bitwarden.  
Copy content of secrets cf.key and cf.crt from bitwarden.  
Create secret
```bash
kubectl create secret tls cf-tls --cert=cf.crt --key=cf.key
```
After creating a secret don't forget to remove your temporary folder.
```bash
cd
rm -rf /tmp/deleteme
```
## Deploy helm chart
Enter helm directory `del-lv` and enter deploy command:
```bash
helm install dellv .
```

# Known issues

# TODO

