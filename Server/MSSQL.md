## Install MSSQL for Ubuntu:

**Adding a key for Microsoft packages**
```
sudo apt install -y software-properties-common;
```
```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -;
```
**MSSQL 2019:**
```
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-2019.list)"
```
**MSSQL 2022:**
```
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-2022.list)"
```
**MSSQL Preview:**
```
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-preview.list)";
```
**Install:**
```
sudo apt-get update && sudo apt-get install -y mssql-server;
```

**Configurations**
```
sudo /opt/mssql/bin/mssql-conf setup;
```