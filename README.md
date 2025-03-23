# How to use
```
Service file
elasticsearch_snapshot_exporter.service

[Unit]
Description=elasticsearch_snapshot_exporter
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=root
Group=root
Type=simple
RestartSec=5s
ExecStart=/usr/local/bin/elasticsearch_snapshot_exporter_amd64 --port 9097 --config /usr/local/bin/es_snapshot.txt --timeout 120 --auth /usr/local/bin/es_snapshot_auth.txt
SyslogIdentifier=elasticsearch_snapshot_exporter
Restart=always

[Install]
WantedBy=multi-user.target



cat es_snapshot_auth.txt (auth for exporter)
username:password

cat es_snapshot.txt (elasticsearch API auth)
elasticsearch clustername,elasticsearch api url,APIusername,APIpassword
```
