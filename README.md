# Zabbix-DHT11
Monitoring DHT11 with Zabbix

Collect temperature and humidity data from DHT11 sensor connected to RPi.

<b>Details of operation:</b>
1. The "query schedule" item send a request to dht.query agent key.
2. The agent run the assigned key command (dfy_split.pl) with given parameters.
3. The script get datas from DHT11, format them for the zabbix_sender and send.
4. The Zabbix server receives the values and work with defined trapper items.

<b>Install:</b>
1. Copy "<tt>userparameter_dht.conf</tt>" on RPi to Zabbix agent userparameter config directory and restart agent.
2. Copy "<tt>dfy_split.pl</tt>" to RPi <tt>/usr/bin/</tt>. If use other directory, then please modify the path in userparameter_dht.conf.
3. Install DHT11 from DHT repository. 
4. Load the "<tt>DHT_sensors_template.xml</tt>" in Zabbix server, change in query schedule item the "<tt>zabbix.mydomain.hu</tt>"
string to your Zabbix server name and assign template to RPi.
5. Enjoy!

<b>Tested environment:</b><br>
RPi3B+ Linux 4.19.66-v7+, Zabbix 4.2
