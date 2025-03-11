# Bash Vulnerability Scanner 

1. Initial Port Scan
  * output > open_ports.txt

2. Extract Open Ports
  * process open_ports and generate list

3. Run Nmap Vulnerability Scan
  * vuln, vulners, ssh-auth-methods
  * output > nmap_vuln_results.txt

4. Default Credentials Check
  * SSH
    * root, toor
  * FTP
    * anonymous, anonymous@
  * MySQL
    * root, root

5. Service Version Detection and CVE Query
  * For each service, the script queries CVEs based on the software and version running on the open ports
  * curl to query NVD API 
  * jq for processing JSON responses
