# IP space
https://reverse.report/
```
nslookup host
```

```
host host
```

```
dig domain
```

```
whois host
```
Shodan.io
# subdomains
1. amass
2. virustotal
3. (nslookup wildcards before) massdns 
4. altdns
5. auatone screenshots
```
curl --request GET   --url 'https://www.virustotal.com/vtapi/v2/domain/report?apikey=&domain=trello.com'
```

```
cat ~/projects/trello/recon/massdns_input | bin/massdns -r lists/resolvers.txt -t A -o S -q -w ~/projects/trello/recon/massdns_output
```

```

/amass enum -d trello.com

```

```
./altdns.py -i ~/bugbounty/trello/domain.txt -o ~/bugbounty/trello/subdomains.altdns
python2.7 -m altdns -i subdomains.txt -o altdns.tmp -w ~/wordlists/altdns/words.txt -r -s altdns.out
```
https://www.virustotal.com/gui/domain/trello.com/relations
https://securitytrails.com/
# Ports
```
nmap
-sT TCP Connect
-sS TCP SYN
-sU UDP


-A detect OS and services
-sV standard service detectio


-oN default output
-oX XML
-oG greppable
-oA all


--top-ports
```
masscan
# files/directories
```
./dirsearch.py -u https://trello.com -w ~/pentests/projects/trello/wordlist_cdi.txt -r -R 4 -c 'JSESSIONID=asd; session=qwe' -F -e html,jsp --plain-text-report='/home/gniedziela/pentests/projects/trello/dirsearch.out'
```

```
wfuzz -w ~/wordlists/SecLists/Discovery/Web-Content/raft-large-directories.txt -u https://api.butlerfortrello.com/FUZZ -p 127.0.0.1:8080 --hh 54 --hc 400,404
wfuzz -w ~/pentests/tools/wordlists/ -b JSESSIONID= -p 127.0.0.1:8080 --hc 404 https://host.com/FUZZ
```


```
python ~/pentests/tools/Sublist3r/sublist3r.py -d trello.com -b
```

```
gobuster -p http://127.0.0.1:8080 -u https://api.butlerfortrello.com -k -fw -w ~/wordlists/SecLists/Discovery/Web-Content/raft-medium-directories.txt
```
LinkFinder
# Other
```
cat subdomains.txt | head -n$i | tail -n1000 | aquatone -http-timeout 30000 -out aquatone$i.d -proxy http://127.0.0.1:8080 -ports 443
```

```
curl -s "http://web.archive.org/cdx/search/cdx?url=api.butlerfortrello.com/*&output=text&fl=original&collapse=urlkey"
```
https://github.com/tehryanx/sourcemapper  - reverse .js.map file
https://github.com/x90skysn3k/brutespray
https://github.com/michenriksen/gitrob
https://github.com/random-robbie/keywords/blob/master/keywords.txt
```
theharvester -d domain -b all -f harvester.out     
```

```
nikto -host host
```

```
Censys
```

```
Zoomeye
```

```
https://www.netcraft.com/
```

```
VirusTotal
```

```
RiskIQ
```

```
CRT.SH
```
http://bgp.he.net
TravisCI secrets: https://github.com/lc/secretz
https://osintframework.com/
https://github.com/redhuntlabs/Awesome-Asset-Discovery