# docker-simple-elasticsearch-cluster
Provision a *realistic* elasticsearch cluster from scratch locally or on real servers with some sensible constraints:
- 3 node containerized ElasticSearch cluster, one per host (ES uses lots of resources!)
- ElasticHQ plugin running in ElasticSearch
- Kibana container on each host
- Configure each host to have correct ulimit to the docker user etc. settings for optimal ES running
- Can pass in config file to ES (config/elasticsearch.yml) rather than a long complicated string of command line arguments
- Elasticsearch's config file contains list of hosts to form a unicast cluster
- Persistent mounted data volume (when your container dies you don't lose all your data)


## make local virtual machines (optional)
- Run this to make 3 on your local machine with docker-machine.
- Fixes up boot2docker image to be like any normal linux (python installed for ansible)
```
.\make-the-virtual-machines.sh
```

## create the cluster
make sure inventory.ini matches your machines (local virtual or real servers)
```
ansible-playbook create-es-cluster.yml
```
