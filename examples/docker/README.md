# running with docker compose

Battaries included
------------------

* [influxdb](https://www.influxdata.com/) - for nudnik metrics
* [grafana](https://grafana.com/) + datasource preconfigured
* nudnik-server with fixed config for influxdb metrics, see `./nudnik/config/server.yml`
* nudnik-server with fixed config for influxdb metrics, see  `./nudnik/config/client.yml`

Start nudnik-demo-stack:
------------------------
```sh
docker-compose up -d
```
* [influxdb](https://www.influxdata.com/) -> http://127.0.0.1:8086
* [grafana](https://grafana.com/) -> http://127.0.0.1:3000
* `nudnik-server` -> http://127.0.0.1:5410

Stop stack:
-----------
```sh
docker-compose down
```

Tweak client / server configs:
------------------------------

see `./config` directory.

In order to see all supported flags run the following command:
```
docker run salosh/nudnik:latest --help
usage: nudnik [-h] [--config-file CONFIG_FILE] [--host HOST] [--port PORT]
              [--server] [--name NAME]
              [--name-mismatch-error {prefix,suffix,exact}] [--meta META]
              [--workers WORKERS] [--streams STREAMS]
              [--initial-stream-index INITIAL_STREAM_INDEX]
              [--interval INTERVAL] [--rate RATE] [--count COUNT]
              [--chaos CHAOS] [--load load_type load_value]
              [--retry-count RETRY_COUNT] [--fail-ratio FAIL_RATIO] [--ruok]
              [--ruok-port RUOK_PORT] [--ruok-path RUOK_PATH]
              [--metrics {stdout,file,influxdb,prometheus}]
              [--metrics-interval METRICS_INTERVAL] [--file-path FILE_PATH]
              [--influxdb-socket-path INFLUXDB_SOCKET_PATH]
              [--influxdb-database-name INFLUXDB_DATABASE_NAME] [--debug]
              [--verbose] [--version]

Nudnik - gRPC load tester

optional arguments:
  -h, --help            show this help message and exit
  --config-file CONFIG_FILE, -f CONFIG_FILE
                        Path to YAML config file
  --host HOST, -H HOST  host
  --port PORT, -p PORT  port
  --server, -S          Operation mode (default: client)
  --name NAME, -n NAME  Parser name
  --name-mismatch-error {prefix,suffix,exact}
                        Fail request on name mismatch (default: None)
  --meta META, -M META  Send this extra data with every request
  --workers WORKERS, -w WORKERS
                        Number of workers (Default: Count of CPU cores)
  --streams STREAMS, -s STREAMS
                        Number of streams (Default: 1)
  --initial-stream-index INITIAL_STREAM_INDEX
                        Calculate stream ID from this initial index (Default:
                        0)
  --interval INTERVAL, -i INTERVAL
                        Number of seconds per stream message cycle (Default:
                        1)
  --rate RATE, -r RATE  Number of messages per interval (Default: 10)
  --count COUNT, -C COUNT
                        Count of total messages that should be sent (Default:
                        0 == unlimited)
  --chaos CHAOS, -c CHAOS
                        Compute statistical process level random crashes [0,
                        3600/interval] (Default: 0)
  --load load_type load_value, -l load_type load_value
                        Add artificial load [rtt, rttr, cpu, mem, cmd, fcmd]
                        (Default: None)
  --retry-count RETRY_COUNT
                        Number of times to re-send failed messages (Default:
                        -1, which means infinite times)
  --fail-ratio FAIL_RATIO
                        Percent of requests to intentionally fail (Default: 0)
  --ruok, -R            Enable "Are You OK?" HTTP/1.1 API (default: False)
  --ruok-port RUOK_PORT
                        "Are You OK?" HTTP/1.1 API port (default: 80)
  --ruok-path RUOK_PATH
                        "Are You OK?" HTTP/1.1 API path (Default: /ruok)
  --metrics {stdout,file,influxdb,prometheus}, -m {stdout,file,influxdb,prometheus}
                        Enable metrics outputs (Default: None)
  --metrics-interval METRICS_INTERVAL
                        Number of seconds per metrics cycle (Default: 1)
  --file-path FILE_PATH, -F FILE_PATH
                        Path to exported metrics file (Default:
                        ./nudnikmetrics.out)
  --influxdb-socket-path INFLUXDB_SOCKET_PATH
                        Absolute path to InfluxDB Unix socket (Default:
                        /var/run/influxdb/influxdb.sock)
  --influxdb-database-name INFLUXDB_DATABASE_NAME
                        InfluxDB database name (Default: nudnikmetrics)
  --debug, -d           Debug mode (default: False)
  --verbose, -v         Verbose mode, specify multiple times for extra
                        verbosity (default: None)
  --version, -V         Display Nudnik version

2018 (C) Salo Shp <https://github.com/salosh/nudnik.git>
```


Make sure you go the correct version ...

```
docker run salosh/nudnik:latest -V
Nudnik v0.0.21 - 2018 (C) Salo Shp <https://github.com/salosh/nudnik.git>
```
