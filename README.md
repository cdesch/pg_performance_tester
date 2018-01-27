# pg_performance_tester




64 gigs of memory
2 x XEON E5-2620 @ 2.00 Ghz x24
9.5.10
listen_addresses = 'localhost'          
listen_addresses = '*'          

max_connections = 100
max_connections = 200

shared_buffers = 128MB  
shared_buffers = 16GB


effective_cache_size = 4GB
effective_cache_size = 48GB

default_statistics_target = 100

min_wal_size = 1GB
max_wal_size = 2GB
checkpoint_completion_target = 0.7
wal_buffers = 16MB

maintenance_work_mem = 16MB
maintenance_work_mem = 2GB

work_mem = 1MB
work_mem = 83886kB

random_page_cost = 1.1



pgbench -i -s 15 bench1
pgbench -c 4 -j 2 -T 600 bench1 

pgbench -i -s 70 bench2
pgbench -c 4 -j 2 -T 600 bench2 -P 5
pgbench -c 4 -j 2 -T 600 -S bench2 -P 10
pgbench -c 4 -j 2 -T 600 -N bench2 -P 10


pgbench -i -s 600 bench3
pgbench -c 4 -j 2 -T 600 bench3 -P 10


pgbench -i -s 30 bench
pgbench -c 1 -T 600 bench
pgbench -c 8 -j 2 -T 600 bench
pgbench -c 64 -j 4 -T 600 bench
pgbench -c 64 -j 4 -T 600 -N bench

# Batch DB Setup

pgbench -i -s 15 bench1; pgbench -i -s 70 bench2; pgbench -i -s 600 bench3; pgbench -i -s 30 bench

create database bench;
create database bench1;
create database bench2;
create database bench3;


