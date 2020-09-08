# NMAP
This project is my implementation of the port scanner: nmap

## RESUME
Nmap is a free port scanner created by Fyodor and distributed by Insecure.org.

He is designed to detect open ports, identify hosted services, and obtain
information about the operating system of a remote computer.

This software has become a benchmark for network administrators because auditing
Nmap's results provides information on the security of a network.

It is available on Windows, Mac OS X, Linux, BSD and Solaris.

## BEHAVIOUR
```sh
gbourgeo@debian:~/Work/nmap2me$ ./ft_nmap -h
Usage: ft_nmap [OPTIONS]...

	-d, --debug
		Debug mode

	-e, --interface [name]
		Specify the interface to use

	-f, --file [filename]
		File name containing IP addresses to scan

	-h, --help
		Print this help screen and return

	-i, --ip [address]
		Ip address to scan in dot format

	-if, --iflist
		Print host interfaces and routes

	-p, --ports [range]
		[1024 max] Ports to scan (eg: 1-10 or 1,2,3 or 1,5-15)

	-r, --retry [number]
		Number of retry to send packets

	-s, --speedup [rate]
		[250 max] Number of parallel threads to use

	-S, --scan [type]
		SYN/NULL/FIN/XMAS/ACK/UDP

	-t, --timeout [value]
		[1000 default] Wait time for host answer in milliseconds.
		Specify the seconds, minutes or hours by adding s, m or h at the end (eg. 10s, 1m, 1h)

	-v, --verbose
		Verbose mode
```

+ This implementation uses the **libpcap** and **libpthread** libraries to capture network packet.
+ The executable is nammed __ft_nmap__.
+ Only IPv4 is handled.
+ Handle FQDN without DNS resolution.
+ Possibility to choose the number of threads. Minimum: 0, maximum: 250.
+ Possibility to read IP's from a file.
+ Type of scan supported:
  - SYN
  - NULL
  - ACK
  - FIN
  - XMAS
  - UDP
  
  If none is specified, the 6 types are used.
+ Ports scan can be passed individually or by range or both (eg. 100,200,300 or 100-200 or 100-200,300)
  
  If none is specified, the port scan range will be 1-1024.
  
  The limit number of ports to be scan is 1024.
  
```sh
gbourgeo@debian:~/Work/nmap2me$ sudo ./ft_nmap -i 127.0.0.1
[sudo] Mot de passe de gbourgeo : 

Starting ft_nmap at 2020-09-08 16:08 CEST

-- Scan Configurations --
Target IP-Address     : 127.0.0.1
No of Ports to scan   : 1024
Scan performed        : SYN NULL FIN XMAS ACK UDP 
No of threads         : 1
No of retry           : 2
Scan delay            : TCP 1000

ft_nmap scan report for 127.0.0.1 (127.0.0.1)
PORT      STATE    
21/tcp    open    
22/tcp    open    

Not shown: 5118 closed ports
```

## AUTHOR
+ Gilles BOURGEOIS
