# installation-hadoop-Namenode-3-datanode-avec-docker


Pour le lancer :
Dans le repertoire ou le Dockerfile se trouve   

docker build -t v1   
 
docker run -it --rm -h NameNode --add-host Namenode:127.0.1.1 --name karimh1  -p 50010:50010 -p 50020:50020 -p 50070:50070 -p 50075:50075 -p 50090:50090 -p 8020:8020 -p 9000:9000 -p 10020:10020 -p 19888:19888 -p 8030:8030 -p 8031:8031 -p 8032:8032 -p 8033:8033 -p 8040:8040 -p 8042:8042 -p 8088:8088 -p 49707:49707 -p 2122:2122 -p 50012:50012 -p 50013:50013 -p 50014:50014 -p 50076:50076 -p 50021:50021 -p 50077:50077 -p 50022:50022 -p 50023:50023 -p 50078:50078 v1   


Une fois le docker lancé : 

service ssh restart && ssh localhost   

## Formattage et lancement du namenode
cd /usr/local/hadoop && ./bin/hadoop namenode -format  
./bin/hdfs namenode  

## Formattage et lancement des datanodes  
Sur une nouvelle fenetre:   
docker ps -a.  

Recuperer <id> . ouvir 3 fenetres, pour chacun des datanodes  
docker exec -it <ID-Container>  bash (Sur les 3 fenetres)

/usr/local/hadoop/bin/hdfs datanode start 

## lancement des datanodes . 

cd /usr/local/hadoop && ./bin/hdfs datanode -conf ./etc/hadoop/datanode1.xml   
cd /usr/local/hadoop && ./bin/hdfs datanode -conf ./etc/hadoop/datanode2.xml  
cd /usr/local/hadoop && ./bin/hdfs datanode -conf ./etc/hadoop/datanode3.xml   


#### Aide. Se placer dans dossier hadoop . 
./bin/hdfs dfsadmin -report     
./bin/hdfs fcsk /   
./sbin/start-all.sh  
 
 
### Changer valeur IP des datanodes
./bin/hdfs datanode -D "dfs.datanode.address=50013" -conf ./etc/hadoop/datanode1.xml   
