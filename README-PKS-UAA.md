# Make PKS Users (with UAAC)
- Ops Manager > PKS > Get TLS Cert + UAA Admin Credential
- ssh ubuntu@ops.dojo3.coinfra.net
- uaac target api.pks.dojo3.coinfra.net:8443 --ca-cert pks.crt
- uaac token client get admin -s ADMIN-CLIENT-SECRET (Pks Uaa Management Admin Client)
- uaac user add selo --emails selo@coinone.com -p PASSWORD
- uaac member add pks.clusters.manage selo
- pks login -a api.pks.dojo3.coinfra.net -u selo -p PASSWORD -k
