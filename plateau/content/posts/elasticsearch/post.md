As addendum to the previous post about corrupt Elasticsearch Shards, here is the command to increase your shard replicas.

For the entire cluster; for craps sake make sure you have enough disk space for this:

    curl -XPUT 'localhost:9200/_settings' -d  '{ "index" : { "number_of_replicas" : 2 } }'

For a specific index use this command:

    curl -XPUT 'localhost:9200/<index_name>/_settings' -d  '{ "index" : { "number_of_replicas" : 2 } }'