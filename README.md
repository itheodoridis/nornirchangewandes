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

Here are some links that may prove usefull in understanding how to put things together.
I am on twitter at @mythryll . 
https://nornir.readthedocs.io/en/stable/tutorials/intro/overview.html this is the Nornir documentation, the files are available in github. If you are new at Network Automation and have no knowledge of Python, this is not the place to start. I will throw some python links in the end. You can understand most of what you need, if you have somewhat familiar with python (variables, control structures, functions, lists, dictionaries) and some idea about what Netmiko and Napalm are. There is a great introductory video about Napalm and Nornir by Stuart Clark through the NetDevOps Live Youtube Channel
https://youtu.be/3uIk0WQLHZk 
or better yet check them out at the cisco netdevops live pages where all the sessions from the show are available and you can subscribe for the upcomming ones:
https://developer.cisco.com/netdevops/live/ over here you can watch the first videos of each season presented by Hank Preston, so you can get an easy introduction.
If you want to start with Network Automation I would suggest you start with Kirk Byers website
https://pynet.twb-tech.com/blog/automation/netmiko.html Netmiko supports connections to a lot of network devices of different types and vendors. Check them out.
https://pynet.twb-tech.com/ Start here for an overall view.
Kirk is doing an email course for Python for Network Engineers which is free (great stuff, you will learn a lot) but also gives a paid course which is more advanced. I can't afford it yet (I am not expecting my network automation knowledge to pay off, it's about where I work), but I have take a look at some of the source code so I highly recommend getting in that if you can.
In Kirk's website you can pick up two additionall threads of information:
- Netmiko and Textfsm (NTC-Templates too): great stuff, it's a whole project available also on github, basically you can parse almost everything you can think of that is a result of a command send to a network device. It usually comes back as a list of dictionaries that you can navigate to get to the fields you want. The template files themselves contain the fields that are parsed. There are other parsers of coure, the Genie parser from the PyATS & Genie project is probably the most promising one. https://github.com/networktocode/ntc-templates
- Introduction to Nornir: It's a collection of two articles staring from this one https://pynet.twb-tech.com/blog/nornir/intro.html and moving on to this https://www.linkedin.com/pulse/using-nornir-os-upgrades-part-2-kirk-byers/

Chec the Nornir discourse page at https://nornir.discourse.group/ It's the forum to sign in and ask your questions. 
If you like slack, the there is the NetworktoCode workspace and from there you can find the Nornir channel at https://networktocode.slack.com/messages/C82409LEL . Live discussion. I like it!
I have posted some content at my blog http://www.mythryll.com . It's a personal one, nothing fancy, I can't afford fancy sites so no impressive pics and videos there, but there are things to look at and get ideas on how to pick up and use things. I have a lot of legacy gear to manage so it might be usefull to you if you are in the same position. I will move some of that in repositories as well, soon.

I got a lot of help by Dmitry Figol for this one (of course I had to understand his input and adapt it to my needs, also figure out some missing links) and very usefull advice by Nick Russo. They are both on twitter and quite famous in the NetDevOps world so no need to provide links to them here. One of the pieces of advice I got is to use ipdb. I used the Nornir page for that to get started: https://nornir.readthedocs.io/en/stable/howto/ipdb_how_to_use_it_with_nornir.html . It's true it can change everything on how you figure out things work.

Best of luck in you efforts, learning is the way forward (learn as much as you can and for as long as you can), and giving back of course! Ty all.

[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/itheodoridis/nornirchangewandes)
