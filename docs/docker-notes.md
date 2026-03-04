# Docker Notes — Day 9

## Docker Version

[$ docker version
Client:
 Version:           28.3.2
 API version:       1.51
 Go version:        go1.24.5
 Git commit:        578ccf6
 Built:             Wed Jul  9 16:12:31 2025
 OS/Arch:           windows/amd64
 Context:           desktop-linux
]

## Hello World Test

[$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete
Digest: sha256:ef54e839ef541993b4e87f25e752f7cf4238fa55f017957c2eb44077083d7a6a
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
]

## Postgres Container
Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine
#docker ps

Output:

CONTAINER ID IMAGE STATUS PORTS NAMES
postgres:15-alpine Up 0.0.0.0:5432->5432/tcp pg-prework

Startup Logs
#docker logs pg-prework

Important confirmation line:

LOG: database system is ready to accept connections
# docker stop pg-prework
#docker restart pg-prework
#docker logs pg-prework
pg-prework
pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-02 23:24:08.008 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
waiting for server to start....2026-03-02 23:24:09.785 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 23:24:09.788 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 23:24:09.802 UTC [44] LOG:  database system was shut down at 2026-03-02 23:24:09 UTC
2026-03-02 23:24:09.815 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down...2026-03-02 23:24:09.876 UTC [41] LOG:  received fast shutdown request
.2026-03-02 23:24:09.880 UTC [41] LOG:  aborting any active transactions
2026-03-02 23:24:09.885 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-02 23:24:09.886 UTC [42] LOG:  shutting down
2026-03-02 23:24:09.889 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-02 23:24:09.912 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.006 s, sync=0.003 s, total=0.027 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-02 23:24:09.926 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-02 23:24:10.036 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 23:24:10.036 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-02 23:24:10.036 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-02 23:24:10.042 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 23:24:10.052 UTC [55] LOG:  database system was shut down at 2026-03-02 23:24:09 UTC
2026-03-02 23:24:10.066 UTC [1] LOG:  database system is ready to accept connections

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 02:39:50.808 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 02:39:50.808 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 02:39:50.809 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 02:39:50.820 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 02:39:50.835 UTC [29] LOG:  database system was interrupted; last known up at 2026-03-02 23:24:10 UTC


#Issues Encountered

None
