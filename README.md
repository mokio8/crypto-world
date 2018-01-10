# crypto-world
Standardize common cryptocurrency related tasks 

# supported O.S
- Ubuntu 16.x

# supported coins
- Ethereum
- Hush
- Trezarcoin


# supported miners
- ccminer
- ethminer
- ewbf
- nheqminer

# build commands
##### run from the build/ directory
- make rig-nvidia

# Mining Commands
##### run from the mine/ directory
- make mine-{coin} i.e (make mine-hush)

# Logstash (optional)
```
sudo  service filebeat start
cd /usr/share/logstash; sudo bin/logstash -f crypto-world-mines.conf  --path.settings /etc/logstash/ --config.reload.automatic
```

# Configuration (config/)
- update the rig name by changing fields.rig in filebeat.yml
- crypto-world-mines.conf:
-- change output.elasticsearch.host to the explorer url
- filebeat.yml
-- change fields.rig to this rigsname (use unique and meaningful names) 
  

# Ubuntu Install
```
sudo apt-get install git -y
mkdir -p /opt
sudo chown -R $USER:$USER /opt/
git clone https://github.com/mokio8/crypto-world.git /opt/crypto-world
cd /opt/crypto-world/build
```
