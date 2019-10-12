docker run -d --name some-clickhouse-server --ulimit nofile=262144:262144 $PWD/config.xml:/etc/clickhouse-server/config.xml yandex/clickhouse-server

