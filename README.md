# lazyrecon_docker
Containerized version of my fork of Nahamsec's Lazyrecon.

I'm sure I can optimize the build process and I'm willing to bet I'm not following best practices. I also still need to work out the volume mount and see if its a permission problem or if its because I have a .gitignore in the lazyrecon_results folder and Docker doesn't know how to handle a non-empty folder or if it's because of all my RUN statements in the build process that happen before the volume mount.

# How to run
1) Clone the repo
2) docker build -t lazyrecon .
3) docker run -v lazyrecon_results:/home/lazyrecon_user/tools/lazyrecon/ lazyrecon -d DOMAIN.TLD
4) ???
5) Hopefully profit?!


# soaringswine's Lazyrecon fork
soaringswine: I've added amass and dnsgen into the mix and there was some issues with how cat and sort were being used that would leave the $domain.txt file blank, so I fixed those. Also removed one of the $domain.txt cats that was undoing the wildcard dupe pruning and added some echos to help understand what's going on in different stages.

```
  _     ____  ____ ___  _ ____  _____ ____ ____  _
 / \   /  _ \/_   \\  \///  __\/  __//   _Y  _ \/ \  /|
 | |   | / \| /   / \  / |  \/||  \  |  / | / \|| |\ ||
 | |_/\| |-||/   /_ / /  |    /|  /_ |  \_| \_/|| | \||
 \____/\_/ \|\____//_/   \_/\_\\____\\____|____/\_/  \|

```

# Usage

`./lazyrecon.sh -d target.com`

# About

LazyRecon is a script written in Bash, it is intended to automate some tedious tasks of reconnaissance and information gathering.
This tool allows you to gather some information that should help you identify what to do next and where to look.


# Main Features 
- Create a dated folder with recon notes
- Grab subdomains using:

      * Sublist3r, certspotter and cert.sh
      * Dns bruteforcing using massdns
      
- Find any CNAME records pointing to unused cloud services like aws
- Probe for live hosts over ports 80/443
- Grab a screenshots of responsive hosts 
- Scrape wayback for data:

      * Extract javascript files
      * Build custom parameter wordlist, ready to be loaded later into Burp intruder or any other tool
      * Extract any urls with .jsp, .php or .aspx and store them for further inspection
      
- Perform nmap on specific ports 
- Get dns information about every subdomain
- Perform dirsearch for all subdomains 
- Generate a HTML report with output from the tools above
- Improved reporting and less output while doing the work
- Dark mode for html reports


# New features
- Directory search module is now MULTITHREADED (up to 10 subdomains scanned at a time)
- Enhanced html reports with the ability to search for strings, endpoints, reponse sizes or status codes

# DEMO
![cli output](https://github.com/plenumlab/lazyrecon/raw/dev/upgrade/recon.gif)
=================================================================================
![report demo](https://github.com/plenumlab/lazyrecon/raw/dev/upgrade/report.gif)


# Installation & Requirements
- Download the install script from https://github.com/nahamsec/bbht.
- Go version 1.10 or later.

### System Requirements
- Recommended to run on vps with 1VCPU and 2GB ram.



# Authors and Thanks
This script makes use of tools developped by the following people
- [Tom Hudson - Tomonomnom](https://github.com/tomnomnom)
- [Ahmed Aboul-Ela - Aboul3la](https://github.com/aboul3la)
- [B. Blechschmidt - Blechschmidt](https://github.com/blechschmidt)
- [Thomas D. - Maaaaz](https://github.com/maaaaz)
- [Daniel Miessler - Danielmiessler](https://github.com/danielmiessler)


# TO DO
- Report only mode to generate reports for old dirsearch data
- SubDomain exclusion





**Warning:** This code was originally created for personal use, it generates a substantial amount of traffic, please use with caution. 


