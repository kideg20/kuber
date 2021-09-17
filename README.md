# kuber
TESTOVIJ TEKSTS

## CloudFlare secritificate as k8s tls-secret
copy public.crt and private.key somewhere example /tmp/deleteme
## CloudFlare sertificate as k8s tls-secret
kubectl create secret tls cf-tls \
  --cert=cf_del.lv.crt \
  --key=cf_del.lv.key
