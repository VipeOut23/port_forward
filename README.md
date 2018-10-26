# port_forward
This little script is used to quickly setup firewall rules (iptables) to forward ports from a machine to another one in a subnet.

# Basic example
You have your server at `example.org` and want to make a service inside a private network available at `example.org:1000`.
The service is on `10.8.0.10:4444`.
```
./port_forward -a 10.8.0.10:4444 -P 1000
```
You can remove the rules with
```
./port_forward -r 10.8.0.10:4444 -P 1000
```

# Arguments
-a [addr]:[port] append rules for NAT device's [addr] and [port]  
-r [addr]:[port] remove rules (all arguments must be the same as they were, when adding the rule)  
-P [port] port on the NAT device ("from_port") Note: If unset, use the same port as the NAT client  
-g [addr] set the gateway used by the NAT client (if empty, this script tries to guess)  
-d dry run, print commands to stdout  
--post-index=[val] the value used with iptables "-I" argument (for the POSTROUTING chain)  
--pre-index=[val] the value used with iptables "-I" argument (for the PREROUTING chain)  
-h|--help you already know :)  
