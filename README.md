# Cassandra YCSB Tests

## Tests Included
* **csload1** - 100% Writes
* **csload2** - 100% Reads
* **csload3** - 80/20% Read/Write
* **csload4** - 20/80% Read/Write
* **csload5** - 50/50% Read/Write
* **csload-disk-stress-10G** - Loads 10GB of data and reads all
* **csload-disk-stress-25G** - Loads 25GB of data and reads all
* **csload-disk-stress-250G** - Loads 250GB of data and reads all

## Calculating Size of Data
* 1 million records equal 1 GB of data
* Data size multiplied by `fieldlength` property
* 10 million records with `fieldlength=250` equals 25GB of data

## Setup
```
wget https://github.com/brianfrankcooper/YCSB/releases/download/0.12.0/ycsb-0.12.0.tar.gz -O- | tar -xz
cd ycsb-0.12.0/
git clone https://github.com/kenzanlabs/cassandra-ycsb-tests.git
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

 ## LICENSE
Copyright 2017 Kenzan, LLC <http://kenzan.com>
 
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
 
    http://www.apache.org/licenses/LICENSE-2.0
 
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.