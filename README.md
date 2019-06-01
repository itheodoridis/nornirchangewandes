# nornir change wandes
Use nornir to change the description for the wan interface on a group of routers. 
The new descriptions are read from an excel file where there are data corresponding to the site code, the ip address and the circuit numbers (primary and backup combined, because the service is provided from a cpe provider router connected through the gi0/0/1 interface -wan).
So the script demonstrates:
- how to read data from an excel file, 
- how to setup a small project with Nornir defining hosts.yaml, groups.yaml, config.yaml and defaults.yaml files
- how to insert information for each host dynamically in the inventory
- how to define a group of tasks to be run across all the hosts in the inventory
- how to use netmiko to send commands using ntc-templates for the parsing, send config commands and save configuration per host. Keep in mind though that the task is run all at once and concurrently. It took the script about 17 seconds to complete, almost 1 second per host if we want to devide that time per number of hosts.

What is not in the script but was provided as help to me, is how to use the ipdb (the interactive python debugger) to find out how the resulst of the tanks and the inventory itself are structured.
I will update with links for where the documentation can be found for everything.

[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/itheodoridis/nornirchangewandes)
