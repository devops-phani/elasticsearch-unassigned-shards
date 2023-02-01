# elasticsearch-unassigned-shards

- https://stackoverflow.com/questions/19967472/elasticsearch-unassigned-shards-how-to-fix

I also encountered similar error. It happened to me because one of my data node was full and due to which shards allocation failed. If unassigned shards are there and your cluster is RED and few indices also RED, in that case I have followed below steps and these worked like a champ.
in kibana dev tool-

```
GET _cluster/allocation/explain
```

If any unassigned shards are there then you will get details else will throw ERROR.

simply running below command will solve everything-

```
POST _cluster/reroute?retry_failed
```
