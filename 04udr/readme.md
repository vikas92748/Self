1. create the vnet
2. deployed VM
3. create the route table and define the route.
4. associated the created route to subnet.
5. Enable the IP forwarding on the NVA.
6. Add the registery entry on NVA if its a Win
	set-itemProperty -path HKLM:\System\currentcontrolset\services\tcpip\parameters -Name IpEnableRouter -value 1
5. Disable FW on vm or create the Rule for ICMP on VMs.
