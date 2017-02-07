# Cassandra YCSB Tests

## Tests Included
* **csload1** - 100% Writes
* **csload2** - 100% Reads
* **csload3** - 80/20% Read/Write
* **csload4** - 20/80% Read/Write
* **csload5** - 50/50% Read/Write
* **csload-disk-stres-10G** - Loads 10GB of data and reads all
* **csload-disk-stres-25G** - Loads 25GB of data and reads all
* **csload-disk-stres-250G** - Loads 250GB of data and reads all

## Calculating Size of Data
* 1 million records equal 1 GB of data
* Data size multiplied by `fieldlength` property
* 10 million records with `fieldlength=250` equals 25GB of data

## Setup
```
wget https://github.com/brianfrankcooper/YCSB/releases/download/0.12.0/ycsb-0.12.0.tar.gz -O- | tar -xz
cd ycsb-0.12.0/
git clone https://github.com/dbathgate/cassandra-ycsb-tests.git
```

## Loading Data
```
./bin/ycsb load cassandra-cql -threads 250 -p hosts="10.25.1.49" -p cassandra.readconsistencylevel=QUORUM -p cassandra.writeconsistencylevel=QUORUM -P cassandra-ycsb-tests/csload1
```

## Testing 250, 500, and 1000 Threads
```
./bin/ycsb run cassandra-cql -threads 250 -p hosts="10.25.1.49" -p cassandra.readconsistencylevel=QUORUM -p cassandra.writeconsistencylevel=QUORUM -P cassandra-ycsb-tests/csload1
./bin/ycsb run cassandra-cql -threads 500 -p hosts="10.25.1.49" -p cassandra.readconsistencylevel=QUORUM -p cassandra.writeconsistencylevel=QUORUM -P cassandra-ycsb-tests/csload1
./bin/ycsb run cassandra-cql -threads 1000 -p hosts="10.25.1.49" -p cassandra.readconsistencylevel=QUORUM -p cassandra.writeconsistencylevel=QUORUM -P cassandra-ycsb-tests/csload1
```
