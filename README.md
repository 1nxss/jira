# Jira + Postgres + Traefik

### Versions:
Jira 8.22.4 | 
Postgres 14.4 | 
Traefik 2.8.0

### Opts 
- Tuned to 8Gb RAM
- Jira & Postgres backup rotation
- Agent running with correct opts
- Let's Encrypt = yes
- Reverse proxy 443 -> 8080

### Recover
Run `jira-restore-application-data.sh` to restore application data if needed.
Run `jira-restore-database.sh` to restore database if needed.

### Deploy & usage commands:
`sudo docker-compose -f jira-docker.yml -p jira up -d`

`sudo docker logs -f containerID"`

`docker exec containerID bash -c "curl ifconfig.me"`


 **application**
```sh
docker exec jira-jira-1 bash -c "java -jar /var/atlassian/jira/bin/atlassian-agent.jar -d -m it.info@hd555.info -n DevIT -p jira -o http://sd.hd555.info -s B25E-XXXX-XXXX-XXXX"
```
**plugin**
```sh
docker exec jira-jira-1 bash -c "java -jar /var/atlassian/jira/bin/atlassian-agent.jar -d -p com.onresolve.jira.groovy.groovyrunner -n DevIT -m it.info@hd555.info -o http://sd.hd555.info -s B25E-XXXX-XXXX-XXXX"
```

### URL
> https://confluence.atlassian.com/jirakb/how-to-customize-files-inside-a-jira-docker-container-1026533922.html
> https://gitee.com/pengzhile/atlassian-agent/tree/master/src/main/java/io/zhile/crack/atlassian/agent
> https://confluence.atlassian.com/jirakb/change-the-server-id-for-an-instance-of-jira-server-285839562.html
