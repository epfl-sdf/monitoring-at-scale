%Monitoring at scale
%Gil Brechbühler
%26 août 2015

# Monitoring d'évènements

### Quel est le problème ?

* On veut récupérer et centraliser les évènements de différentes machines.

\pause

* Sur une architecture dans laquelle des serveurs peuvent être créés et arrêtés à la volée.

\pause

* But : automatiser le monitoring de ces serveurs.

# Monitoring des métriques

### Schéma

\center
\includegraphics[width=12cm]{img/stats_monitoring.png}

### Collectd

* Daemon écrit en C.

\pause

* Plusieurs entrées : /proc, json, SNMP, ... .

\pause

* Plusieurs sorties : rrd, http, carbon, ... .

### Collectd

* Installation facile : le package est dans les dépôts de beaucoup de distributions.

\pause

* Peut exécuter des scripts écrits par l'utilisateur pour récupérer des données.

\pause

* Extensible avec des plugins (C, Python) :
https://collectd.org/wiki/index.php/Table_of_Plugins

### InfluxDB

* Base de données spécialisée pour le stockage de métriques.

\pause

* RocksDB (key-value store) en backend.

\pause

* Utilise un système de série temporelle.

\pause

### InfluxDB

* Installation facile : un simple exécutable dans une archive à décompresser.

\pause

* Accepte différentes entrées : carbon, http, ... .

\pause

* Aucune configuration manuelle à l'ajout d'un client.

### Grafana

* Dashboard pour visualiser les métriques : interface web en javascript.

\pause

* Connexion à InfluxDB supportée : utilise l'API HTTP d'InfluxDB pour faire les requêtes.

\pause

* Simplifie grandement l'écriture de requêtes à InfluxDB.

\pause

* Peux faire des requêtes à Elasticsearch pour corréler les métriques et les logs.

### Comment grandir ?

* Pour monitorer une nouvelle machine, il suffit de configurer Collectd sur cette machine.

\pause

* Configuration décentralisée.

\pause

* InfluxDB est scalable et gère la réplication.

\pause

* Des instances Grafana indépendantes peuvent facilement être créées.

# Centralisation des logs

### Schéma

\center
\includegraphics[width=12cm]{img/logs_monitoring.png}

### Logstash

* Ecrit en ruby, tourne sur JRuby.

\pause

* Prends des logs en entrée.

\pause

* Filtre et traite les logs.

\pause

* Envoie les logs sur la sortie désirée.

### Logstash : traitement des logs

* Fonctionne avec un système de plugins.

\pause

* Grok (filtre) : système d'expressions régulières puissant pour parser les logs.

\pause

* Beaucoup de plugins d'entrées intégrés : file, syslog, tcp, udp, http, lumberjack, twitter, ... .

\pause

* Beaucoup de plugins de sorties intégrés : stdout, udp, tcp, elasticsearch, kafka, email, ... .

### Logstash : workflow

* Entrées : stdin, file, udp, tcp, syslog, .... .

\pause

* Filtres : anonymize, date, drop, mutate, grok, ... .

\pause

* Sorties : stdout, file, udp, tcp, elasticsearch, ... .

### Logstash : exemple Grok

```ruby
filter {
  grok {
    match => { "message" => "(?<syslog_timestamp>%{YEAR}[/-]\
    %{MONTHNUM}[/-]%{MONTHDAY}[ ]%{TIME})\
    %{GREEDYDATA:logmessage}" }
    add_field => [ "received_at", "%{@timestamp}" ]
  }
}
```

### Logstash : configuration

```ruby
input {
    file {
        path => "apache_log.log"
        start_position => beginning
    }
    stdin{}
}
filter {
    grok {
        match => { "message" => "%{COMBINEDAPACHELOG}"}
    }
}
output {
    stdout {codec => rubydebug}
}
```

### Logstash-forwarder

* Beaucoup plus léger que logstash. Ecrit en Go.

\pause

* Prends des fichiers de log en entrée (ou stdin) et envoie les logs sur le réseau via TLS.

### Logstash-forwarder : configuration

Logstash :

```ruby
input {
  lumberjack {
    # The port to listen on
    port => 5514

    # The paths to your ssl cert and key
    ssl_key => "/path/to/key.pem"
    ssl_certificate => "/path/to/cert.pem"
  }
}
```

### Logstash-forwarder : configuration

Logstash-forwarder :

```ruby
{
  "network": {
    "servers": [ "logstash-instance-1:5514",
      "logstash-server-2:5514"],
    "ssl ca": "/path/to/ca.pem",
    "timeout": 10
  },
  "files": [
    {
      "paths": [ "/var/log/*" ],
      "fields": { "type": "syslog" }
  ]
}
```

### Elasticsearch

* Base de donnée se basant sur des indexes.

\pause

* Gère le sharding et la réplication.

### Elasticsearch : sharding et réplication

```ruby
{
    "template" : "logstash-*",
    "settings" : {
        "number_of_shards" : 4,
        "number_of_replicas" : 2
    }
}
```

### Elasticsearch : clustering

* Construction d'un cluster facile.

\pause

* Ajout d'un noeud au cluster facile.

### Elasticsearch : configuration

```ruby
cluster:
  name: presentation-cluster
discovery:
  zen:
    ping:
      multicast:
        enabled: false
      unicast:
        hosts:
          - elasticsearch-instance-1:9300
          - elasticsearch-instance-2:9300
network:
  host: 0.0.0.0
node:
  name: elasticsearch-instance-3
```

### Kibana

* Dashboard pour elasticsearch : interface web en javascript.

### Conclusion

Collectd : https://collectd.org/ \
Collectd table des plugins : https://collectd.org/wiki/index.php/Table_of_Plugins \
InfluxDB : https://influxdb.com/ \
Grafana : http://grafana.org \
Logstash : https://www.elastic.co/guide/en/logstash/current/index.html \
Logstash-forwarder : https://github.com/elastic/logstash-forwarder \
Elasticsearch : https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html \
Kibana : https://www.elastic.co/guide/en/kibana/current/index.html \
