# Bash Vulnerability Scanner 

### Initial Port Scan

  * output > open_ports.txt

### Extract Open Ports

  * process open_ports and generate list

### Run Nmap Vulnerability Scan

  * vuln, vulners, ssh-auth-methods
  * output > nmap_vuln_results.txt

### Default Credentials Check

  * SSH
    * root, toor
  * FTP
    * anonymous, anonymous@
  * MySQL
    * root, root

### Service Version Detection and CVE Query

  * For each service, the script queries CVEs based on the software and version running on the open ports
  * curl to query NVD API 
  * jq for processing JSON responses

### Example Output 

```
Nmap scan report for 192.168.x.x
Host is up (0.014s latency).
Not shown: 65520 closed tcp ports (conn-refused)
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
****/tcp  open  sip
*****/tcp open  *********
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown
*****/tcp open  unknown

Nmap 7.95 scan initiated Tue Mar 11 14:15:30 2025 as: nmap -p- --min-rate=1000 -T4 -oG open_ports.txt 192.168.x.x

Host: 192.168.x.x ()    Status: Up
Host: 192.168.x.x ()    Ports: 21/open/tcp//ftp///, 22/open/tcp//ssh///, *****/open/tcp//sip///, *****/open/tcp//*********///, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////, *****/open/tcp/////        Ignored State: closed (65520)

ssh2-enum-algos:
********************
key_algorithms: 
********************
server_host_key_algorithms:
********************
encryption algorithms: 
********************
mac_algorithms:
********************
compression algorithms:
********************
ssh-auth-methods:
********************
ssh-hostkey:
***********************************

SERVICE_FINGERPRINTS
SERVICE INFO: OS: XXXXXX; Device: XXXXXXX; CPE: XXXXXXX

[*] Vulnerability scan completed. Check nmap_vuln_results.txt for details.
[*] Checking for default credentials...
[*] Checking SSH default credentials...
[*] Checking FTP default credentials...
Anonymous FTP login allowed on 192.168.x.x
[*] Default credential checks completed.
[*] Extracting service versions...
[*] Checking for known vulnerabilities...
Searching CVEs for ftp ******** on port open...
CVE: CVE-XXXX-XXXXX
CVE: CVE-XXXX-XXXXX
CVE: CVE-XXXX-XXXXX
```
