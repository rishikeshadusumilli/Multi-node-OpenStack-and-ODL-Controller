# Multi-node-OpenStack-and-ODL-Controller

Inventory: 

1. SDN Controller - OpenDaylight
2. Southbound Interface (SBI) - BGP
3. Northbound Interface (NBI) - RESTCONF
4. Infrastructure - Multi-Node OpenStack
5. Application - Python and Flask

Multi-node OpenStack - Steps

1.	Installed Ubuntu 16.04 on 2 HP servers
2.	Downloaded the latest version of devstack from github. In the devstack configuration file (local.conf) on the server acting as OpenStack Control/Compute node, enabled services such as neutron, nova, glance, keystone, heat, cinder etc. Only nova service was enabled on the server acting as Compute node. 
3.	Connected the OpenStack Control/Compute node (IPv4 address: 172.16.55.5/16) to the Compute node (IPv4 address: 172.16.44.4/16).
4.	Installed OpenStack on both the servers by stacking devstack.

BGP peering - Steps

1.	Created instances in OpenStack using our automation script. Associated floating IPs (in the range 172.24.4.0/24) to the instances and connected to the external network using a router.
2.	Installed the latest stable version of ODL on an HP server and connected the ODL server to the OpenStack controller (ODL IPv4 address: 29.0.0.2/24, OpenStack controller IPv4 address: 29.0.0.1/24).
3.	Configured static routes in the virtual router, the ODL server and the OpenStack instances in order to ensure reachability between ODL and the instances.
4.	Installed Quagga and configured BGP to form neighbor relationship between ODL and instances.
5.	Ensured successful BGP peering session establishment between ODL and the instances.

Steps:

1.	Run the finalProject.py program to start the Python Flask module.
2.	In a web browser, navigate to the OpenStack controller's IP address (172.16.55.5:8888).
3.	Once the page opens, it will display options to create a network/router and an instance depending upon the customer's requirement.
4.	Click on any of the given buttons on the homepage and fill the details to create a new network or a new instance.
