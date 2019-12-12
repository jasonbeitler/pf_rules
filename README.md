### Note
If you use this method in a corp environment you will still need to enable the GUI Firewall or it could cause isues with MDM. When you do enable the GUI Firewall be sure to untick "Blcok all incomming" and "Enable Stealth Mode". I know it sounds scarry but the PFRules will take over and you will still be protected. 

# pf_rules

This is just a very locked down PF Rule Set. Before you start yelling at me about letting eveything outbound, I am using LittleSnitch for outbound Firewall. 

Here is how to use it

1. $sudo chown root:wheel org.pflockdown*

2. $sudo mv org.pflockdown.conf /etc/pf.anchors

3. $sudo mv org.pflockdown.plist /Library/LaunchDaemons

4. At this point you can either reboot (borning) or run 

    $sudo launchctl load /Library/LaunchDaemons/org.pflockdown.plist

Also if you really want to make your life easier add the following to your .profile

1. alias pfedit='sudo vim /etc/pf.anchors/org.pflockdown.conf'
2. alias pfflush='sudo pfctl -F all'
3. alias pflist='sudo pfctl -sr'
4. alias pfload='sudo launchctl load /Library/LaunchDaemons/org.pflockdown.plist'
5. alias pfunload='sudo launchctl unload /Library/LaunchDaemons/org.pflockdown.plist'
6. alias pftest='sudo pfctl -v -n -f /etc/pf.anchors/org.pflockdown.conf'

* Note some changes were made to Time and DNS. You will need to adjust to fit your needs. Pay close attention to DNS and if you are using a Corporate VPN you will need to add those DNS servers or it will not work. 

Good Luck

And for those that like to see things in action, here are the nmap scans from both UDP and TCP.

#UDP Scan
sudo nmap -sU -Pn -p 1-65535 .50

Starting Nmap 7.31 ( https://nmap.org ) at 2016-11-20 09:47 CST
Nmap scan report for .50
Host is up (0.079s latency).
All 65535 scanned ports on .50 are open|filtered
MAC Address: omitted (Apple)

Nmap done: 1 IP address (1 host up) scanned in 5208.70 seconds

#TCP Scan
sudo nmap -sS -Pn -p 1-65535 .50
Password:

Starting Nmap 7.31 ( https://nmap.org ) at 2016-11-20 08:58 CST
Nmap scan report for .50
Host is up (0.17s latency).
All 65535 scanned ports on .50 are filtered
MAC Address: omitted (Apple)

Nmap done: 1 IP address (1 host up) scanned in 11092.96 seconds
