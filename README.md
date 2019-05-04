# Firewalld Cheatsheet

This project is where I'm going to dump some solutions that I found for common issues that I run into on Firewalld. It's going to be very unorganized to start, but might become something better?

## Add a Firewall Rule restricted by Source IP Address

First, add the firewall rule to the running configuration and test it.

```bash
firewall-cmd --zone=public --add-rich-rule='
  rule family="ipv4"
  source address="1.2.3.4/32"
  port protocol="tcp" port="4567" accept'
```

If you run into issues here, you can simply restart the box and the rule will disappear. Once the rule is tested, go ahead and add it to the system permanently by simply runnning the above again but using `--permanent` before the zone declaration.

```bash
firewall-cmd --permanent --zone=public --add-rich-rule='
  rule family="ipv4"
  source address="1.2.3.4/32"
  port protocol="tcp" port="4567" accept'
```
