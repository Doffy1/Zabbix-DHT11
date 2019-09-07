# Zabbix-DHT11
Monitoring DHT11 with Zabbix

Collect temperature and humidity data from DHT11 sensor connected to RPi.

<b>Details of operation:</b>
1. The "query schedule" item send a request to dht.query agent key.
2. The agent run the assigned key command (dfy_split.pl) with given parameters.
3. The script get datas from DHT11, format them for the zabbix_sender and send.
4. The Zabbix server receives the values and work with defined trapper items.

<b>Install:</b>
1. Copy <tt>userparameter_dht.conf</tt> on RPi to Zabbix agent userparameter config directory and restart agent.
2. Copy <tt>dfy_split.pl</tt> to RPi <tt>/usr/bin/</tt>. If use other directory, then please modify the path in <tt>userparameter_dht.conf</tt>.
3. Increase the <tt>Timeout</tt> to minimum 10 in </tt>/etc/zabbix/zabbix_agentd.conf<tt>.
4. Install DHT11 binary code from <a href=https://github.com/Doffy1/DHT11>DHT11<a> repository.
5. Add the <tt>zabbix</tt> user to <tt>gpio</tt> group in <tt>/etc/group</tt> file.
6. Load the <tt>DHT_sensors_template.xml</tt> in Zabbix server and
    - change in query schedule item the <tt>zabbix.mydomain.hu</tt> string to your Zabbix server name
    - change Humidity and Temperature items alloved hosts value to your RPi (registered in Zabbix) name
 and assign template to RPi.
7. Enjoy!

<b>Tested environment:</b><br>
RPi3B+ Linux 4.19.66-v7+, Zabbix 4.2
