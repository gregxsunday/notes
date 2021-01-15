# Race condition
https://github.com/TheHackerDev/race-the-web
# SSRF
https://blog.assetnote.io/2021/01/13/blind-ssrf-chains/
# SQL
sqlmap
```
sqlmap --url='https://example.com' --header='Content-Type: application/x-www-form-urlencoded' --data='username=admin&password=admin' --proxy=http://127.0.0.1:8080 --risk=3 --dbms='Oracle' --level=5 --method=POST -p username
```
# XSS
* XSS Polyglot https://polyglot.innerht.ml/
* KNOXSS https://knoxss.me/
* XSStrike https://github.com/s0md3v/XSStrike
* Image Attacks https://github.com/doyensec/StandardizedImageProcessingTest
# Subdomain takeover
subjack
```
~/go/bin:$ ./subjack -w ~/bugbounty/trello/services/subdomains.txt -timeout 30 -o ~/bugbounty/trello/services/subjack.txt -ssl -a -m -c ~/pentests/tools/subjack/fingerprints.json
```
https://github.com/haccer/subjack
SubOver
```


```
https://github.com/Ice3man543/SubOver
aquatone
```
cat subdomains.txt | head -n$i | tail -n1000 | aquatone -http-timeout 30000 -out aquatone$i.d -proxy http://127.0.0.1:8080 -ports 443
```
https://github.com/michenriksen/aquatone
https://michenriksen.com/blog/subdomain-takeover-detection-with-aquatone/
# Js analysis
```
eslint host-handlers.js -c ~/pentests/tools/eslint-security-scanner-configs/eslintrc-heavy.js
eslint host-handlers.js -c ~/pentests/tools/eslint-security-scanner-configs/eslintrc-light.js
```
# Template injection

```
python2 tplmap/tplmap.py --proxy=http://127.0.0.1:8080 -u 'https://example.com/errorPage.jsp?seid='
python2 tplmap/tplmap.py --proxy=http://127.0.0.1:8080 -u 'https://example.com/errorPage.jsp?seid=' -e Velocity
```
# SSL
```
nmap --script ssl-cert,ssl-enum-ciphers -p 8443 example.com
```

```
openssl s_client -connect example.com:8443

HEAD / HTTP/1.1
R

HEAD / HTTP/1.1
```

```
mono ~/pentests/tools/TestSSLServer/TestSSLServer.exe https://example.com:8443
```

```
sslyze --regular example.com:8443
```

```
sudo docker run -ti drwetter/testssl.sh example.com:8443
```
# XXE
* https://github.com/BuffaloWill/oxml_xxe
* https://gist.github.com/honoki/d7035c3ccca1698ec7b541c77b9410cf
# MISC
```
parallel -j 4 "do something on {}" :::: my_super_secret_text_file.txt
```
```
cvesearch -s 20xx-xxxx
```
* clearing custom wordlist from noise
https://github.com/BonJarber/SecUtils/blob/master/clean_wordlist/clean_wordlist.sh
* taking the parameter names from js files
https://github.com/Static-Flow/ParameterMiner
# Static analysis
https://github.com/find-sec-bugs/find-sec-bugs
# Image memory leaks
* https://www.sans.org/reading-room/whitepapers/webappsec/uninitialized-memory-disclosures-web-applications-39460
* https://github.com/v-p-b/image-memleak
# HTTP/2 Request smuggling
* https://github.com/BishopFox/h2csmuggler
