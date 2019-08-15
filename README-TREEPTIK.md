Stack k8S :


VERSIONS 		Viconics 							Stack
Bamboo		|	5.15.0.1					|		6.8.1
Jira		|	v7.3.8#73019-sha1:94e8771	|		8.0.2
Confluence	|	6.15.3						|		latest TRES MAUVAIS 
Bitbucket	|	4.11.1						|		latest TRES MAUVAIS
CROWD		|	3.4.5						|		latest TRES MAUVAIS

Bamboo

Vars:
domain : "bamboo.domain.xyz"
nfsserverip "10.1.1.22"
nfspath /root/nfs/bamboo_prod

git add -A
git commit -m "edit"
git push


kubectl -n test apply -f bamboo/bamboo_deploy.yml

kubectl -n test apply -f jira/jira_deploy.yml


kubectl -n test apply -f crowd/prod_crowd_service_fe.yml
kubectl -n test apply -f crowd/prod_crowd_deployment.yml

kubectl -n test apply -f bitbucket/prod_bitbucket_service_fe.yml
kubectl -n test apply -f bitbucket/prod_bitbucket_deployment.yml

kubectl -n test apply -f confluence/prod_confluence_service_fe.yml
kubectl -n test apply -f confluence/prod_confluence_deployment.yml

kubectl -n test apply -f database/prod_database_service_be.yml
kubectl -n test apply -f database/prod_database.yml

GET ALL
kubectl get all  -n test

DELETE ALL
kubectl delete all --all -n test


kubectl delete -f elastic-search-rc.yaml

kubectl delete -f elasticsearch-svc.yaml

kubectl delete -f kibana-rc.yaml

kubectl delete -f kibana-svc.yaml
