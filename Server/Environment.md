## Environment for .net applications

**User creation**
```
sudo adduser --disabled-login --gecos "" zonit;
sudo chgrp -R zonit /home/zonit/;
sudo chown -R zonit:zonit /home/zonit/;
```

**Creation of space**
```
sudo mkdir -p /home/zonit/dev;
sudo mkdir -p /home/zonit/release;
sudo mkdir -p /home/zonit/backup;
```

**Service and startup:**
```
sudo nano /etc/systemd/system/zonit.service;
```
**File contents**
```
[Unit]
Description=System power by Zonit

[Service]
WorkingDirectory=/home/zonit/release
ExecStart=/home/zonit/release/Zonit
ExecStop=/bin/kill ${MAINPID}
Restart=always
# Restart service after 10 seconds if the dotnet service crashes:
RestartSec=10
TimeoutStopSec=10
KillSignal=SIGINT
SyslogIdentifier=Zonit
User=zonit
Environment=ASPNETCORE_ENVIRONMENT=Production
Environment=DOTNET_PRINT_TELEMETRY_MESSAGE=false

[Install]
WantedBy=multi-user.target
```
**Activation and enabling**
```
sudo systemctl enable zonit.service;
sudo systemctl start zonit.service;
```

### Useful commands
**Process status**
```
sudo service zonit status
```
**Process start**
```
sudo service zonit start
```
**Process stop**
```
sudo service zonit stop
```
**Process restart**
```
sudo service zonit restart
```