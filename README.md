# pf_rules

This is just a very locked down PF Rule Set. Here is how to use it

1. $sudo chown root:wheel org.pflockdown*

2. $mv org.pflockdown.conf /etc/pf.anchors

3. $mv org.pflockdown.plist /Library/LaunchDaemons

4. At this point you can either reboot (borning) or run $sudo launchctl load /Library/LaunchDaemons/org.pflockdown.plist

Good Luck
