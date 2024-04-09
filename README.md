In the flowcoll.conf add/modify the following lines

Environment="EF_PROCESSOR_ENRICH_NETIF_SNMP_USERDEF_PATH=/etc/elastiflow/snmp/metadata/user_def.yml"
Environment="EF_PROCESSOR_ENRICH_NETIF_SNMP_USERDEF_REFRESH_RATE=2"

You will need to create the path /etc/elastiflow/snmp/metadata/ 
You will need to create the file /etc/elastiflow/snmp/metadata/user_def.yml

The user_def.yml will include either v2 or v3 statements similar to the following for each device you want to poll. The first IP will be the IP the netflow, IPFIX etc is sourced from. The poll_ip will be the snmp listening IP address. 

192.168.2.2:
  enabled: true
  version:  2
  communities: private
  port:        161
  retries:      3
  timeout:      1000
  poll_ip:     192.168.8.1
192.168.7.1:
  enabled: true
  version: 3
  v3_credential:
    authoritative_engine_boots: 100
    authoritative_engine_time: 200
    username: "elastiflow"
    authentication_protocol: sha
    privacy_protocol: aes
    authentication_passphrase: AaBbCcDdEe1234
    privacy_passphrase: 123456789AaBbCc
  port:        161
  retries:      3
  timeout:      1000
  poll_ip:     192.168.4.3
