# Bug-Bounty-Oneliners
Oneliners curated from my experience and from the internet


### Oneliner to get HTTP Titles:
```bash
for i in $(cat urls.txt ); do echo "$i | $(curl --connect-timeout 0.5 $i -so - | grep -iPo '(?<=<title>)(.*)(?=</title>)')"; done | tee -a titles.txt
```

### Extract subdomains from IP range:
```bash
nmap IP_range | grep "domain" | awk '{print $5}'
```

### Find subdomains and takeover
```bash
subfinder -d {target} >> domains ; assetfinder -subs-only {target} >> domains ; amass enum -norecursive -noalts -d {target} >> domains ; subjack -w domains -t 100 -timeout 30 -ssl -c ~/fingerprints.json -v 3 >> takeover ;
```
