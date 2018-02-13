![Logo](logo.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2018-02-13)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.20|tor-exit0-readme.dfri.se|10
197.231.221.211|exit1.ipredator.se|10
104.223.123.98|unassigned.quadranet.com|10
66.240.192.138|census8.shodan.io|10
71.6.158.166|ninja.census.shodan.io|10
176.10.104.240|tor1e1.digitale-gesellschaft.ch|9
202.137.147.108|ns1.mof.gov.la|9
80.82.77.139|dojo.census.shodan.io|9
71.6.146.186|inspire.census.shodan.io|9
71.6.146.185|pirate.census.shodan.io|9
181.214.87.4|-|9
50.62.139.155|ip-50-62-139-155.ip.secureserver.net|9
222.186.172.48|-|8
180.139.138.165|-|8
191.101.167.250|-|8
80.82.77.33|sky.census.shodan.io|8
113.108.72.2|-|8
93.174.95.106|battery.census.shodan.io|8
125.215.45.157|-|8
122.194.76.132|-|8
119.10.67.206|-|8
103.210.135.136|-|8
185.38.14.171|tor-exit.r2.apx.pub|8
176.10.99.200|-|8
58.61.30.200|-|8
210.121.164.121|-|8
119.10.81.250|-|8
60.173.82.156|-|8
23.129.64.102|xanaduregio.emeraldonion.org|8
43.229.205.182|182.subnet43-229-205.static.inet.net.id|8
219.147.95.246|246.95.147.219.broad.dq.hl.dynamic.163data.com.cn|8
123.150.200.121|-|8
61.153.56.30|-|8
200.109.236.50|200.109.236-50.estatic.cantv.net|8
171.25.193.77|tor-exit1-readme.dfri.se|8
198.20.69.98|census2.shodan.io|8
212.21.66.6|tor-exit-4.all.de|8
171.25.193.78|tor-exit4-readme.dfri.se|8
85.93.20.243|-|8
209.92.176.24|-|8
5.188.10.182|-|8
80.82.64.127|-|8
89.248.172.16|house.census.shodan.io|8
51.15.63.43|tor-exit-proxy.donategrid.com|8
89.248.167.131|mason.census.shodan.io|8
74.106.236.11|static-74-106-236-11.bltmmd.fios.verizon.net|8
27.193.101.252|-|8
221.194.44.211|-|8
125.212.217.215|-|8
125.212.217.214|-|8
149.56.223.241|exit0.liskov.tor-relays.net|8
198.96.155.3|exit.tor.uwaterloo.ca|8
60.191.144.54|-|8
106.250.183.218|-|8
185.94.111.1|-|8
177.73.4.211|177-73-4-211.inbnet.com.br|8
89.234.157.254|marylou.nos-oignons.net|8
176.126.252.12|aurora.enn.lu|8
115.23.187.69|-|8
119.6.204.69|-|8
219.135.58.209|209.58.135.219.broad.fs.gd.dynamic.163data.com.cn|8
5.188.10.179|-|8
