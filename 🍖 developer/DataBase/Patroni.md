
[[🐒 PostgreSQL]] [[High-availability]]

https://medium.com/@chriskevin_80184/high-availability-ha-postgresql-cluster-with-patroni-1af7a528c6be#:~:text=Patroni%20is%20a%20tool%20for,them%20as%20accessible%20as%20possible.

[Patroni](https://github.com/zalando/patroni) is a template for you to create a high-availability (HA) PostgreSQL solution using a combination of PostgreSQL streaming replication and a consensus-based configuration store like etcd, ZooKeeper, or Consul. Your diagram illustrates a three-node Patroni setup, each running an instance of Patroni alongside PostgreSQL.

# Patroni

It provides a template for configuring a highly available PostgreSQL cluster.

Patroni is a tool for managing clusters that can be used to customize and automate the deployment and maintenance of PostgreSQL clusters with high availability. It is written in Python and uses etcd, Consul, and ZooKeeper to store configurations in a way that makes them as accessible as possible. In our setup we will be using etcd.

Patroni can also handle configurations for database replication, backup, and restoration.

Patroni’s settings are managed via the use of a YAML file, which may be stored in any location. In our particular scenario, the configurations will be saved in the `/etc/patroni.yml` file.