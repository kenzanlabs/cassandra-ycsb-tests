# cassandra-ycsb-tests

```
wget https://github.com/brianfrankcooper/YCSB/releases/download/0.12.0/ycsb-0.12.0.tar.gz -O- | tar -xz 
cd ycsb-0.12.0/
git clone https://github.com/dbathgate/cassandra-ycsb-tests.git
./bin/ycsb load cassandra-cql -threads 250 -p hosts="10.25.1.49" -p cassandra.readconsistencylevel=QUORUM -p cassandra.writeconsistencylevel=QUORUM -P cassandra-ycsb-tests/csload1
```
