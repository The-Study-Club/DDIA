## Leaderless replication quorum

Signature arch: 
Amazon Dynamo (Completely different from AWS DynamoDB which is single leader replication)
Cassandra

Features:
client does read repair to update stale data
anti-entropy process: background maintainer constantly checks status and copies missing data between nodes
up-to-date read: k nodes in total, write to m nodes, read from n nodes, m + n > k
example: node_0, node_1, node_2....., node_k, write to node_0 ... node_m, read from node_k-n+1 ... node_k, if m + n > k, then at least one node has up-to-date data. (Pigeonhole principle)