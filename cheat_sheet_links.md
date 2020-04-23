## XSS
https://netsec.expert/2020/02/01/xss-in-2020.html
## Oauth
https://twitter.com/s0md3v/status/1168846854689132544 
## Jenkins
https://github.com/gquere/pwn_jenkins
## Kubernetes
* https://speakerdeck.com/iancoldwater/the-path-less-traveled-abusing-kubernetes-defaults
* https://blog.aquasec.com/dns-spoofing-kubernetes-clusters
* https://github.com/appsecco/attacking-and-auditing-docker-containers-and-kubernetes-clusters
## JWT
https://github.com/ticarpi/jwt_tool/wiki
## Android
https://blog.dixitaditya.com/android-pentesting-cheatsheet/
## DNS rebinding setup
* https://geleta.eu/2019/my-first-ssrf-using-dns-rebinfing/
* https://hackerone.com/reports/541169 -> https://github.com/ajxchapman/sshreverseshell + 
41_gitlab.json
```
[
  {
    "protocol" : "dns",
    "route" : "gitlabext.{domain}",
    "type" : "A",
    "response" : "188.166.76.154"
  },
  {
    "protocol" : "dns",
    "route" : "gitlabextssrf.*",
    "type" : "A",
    "response" : ["{ipv4}", "127.0.0.1"],
    "random" : true,
    "ttl" : 0
  }
]
```
* https://github.com/daeken/httprebind - used for dns rebinding in ssrfs
## Unicode normalization
* https://appcheck-ng.com/unicode-normalization-vulnerabilities-the-special-k-polyglot/
* https://appcheck-ng.com/wp-content/uploads/unicode_normalization.html
* https://eng.getwisdom.io/awesome-unicode/##onetomanycasemappings
## Escalating spring boot actuators to RCE
* 1.x https://www.veracode.com/blog/research/exploiting-spring-boot-actuators
* 2.x https://spaceraccoon.dev/remote-code-execution-in-three-acts-chaining-exposed-actuators-and-h2-database
## Api keys reference
https://github.com/streaak/keyhacks
## AWS
* https://github.com/sa7mon/S3Scanner
* https://github.com/jordanpotti/CloudScraper
* https://github.com/MindPointGroup/cloudfrunt
* https://github.com/RhinoSecurityLabs/pacu
* https://github.com/toniblyx/my-arsenal-of-aws-security-tools
## TravisCI
https://github.com/lc/secretz
## OSINT 
* https://osintframework.com/
* https://github.com/redhuntlabs/Awesome-Asset-Discovery
## Frida scripting guide
https://neo-geo2.gitbook.io/adventures-on-security/frida-scripting-guide/frida-scripting-guide
## Learning new technology
https://learnxinyminutes.com/
## GraphQL
* https://carvesystems.com/news/the-5-most-common-graphql-security-vulnerabilities/
