# coreosPOC
Run a CoreOS cluster on AWS using Cloud Formation

```
# This config is meant to be consumed by the config transpiler, which will
# generate the corresponding Ignition config. Do not pass this config directly
# to instances of Container Linux.

etcd:
  # generate a new token for each unique cluster from https://discovery.etcd.io/new?size=3
  # specify the initial size of your cluster with ?size=X
  discovery: https://discovery.etcd.io/<token>
  # multi_region and multi_cloud deployments need to use {PUBLIC_IPV4}
  advertise_client_urls: http://{PRIVATE_IPV4}:2379,http://{PRIVATE_IPV4}:4001
  initial_advertise_peer_urls: http://{PRIVATE_IPV4}:2380
  # listen on both the official ports and the legacy ports
  # legacy ports can be omitted if your application doesn't depend on them
  listen_client_urls: http://0.0.0.0:2379,http://0.0.0.0:4001
  listen_peer_urls: http://{PRIVATE_IPV4}:2380
  
```
