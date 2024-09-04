Azure NSGs and ASGs
What is NSG
Azure Network Security Groups (NSGs) are utilized to filter network traffic between Azure resources within a virtual network. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. For each rule, you can specify source and destination, port, and protocol.
Azure NSGs control access and manage communication between:
⦁	Individual workloads hosted on one or more Azure VNets.
⦁	Connectivity between on-prem environments and Azure via an Application Gateway, VPN Gateway, Azure Firewall, Azure Bastion service, and Virtual Network Appliances.
⦁	Connections to and from the Internet.
NSGs can be assigned on the Subnet or network interface level however it is important to plan your implementation and establish clear guidelines. If you start placing NSG’s on the subnet and NIC level randomly you may end up in the situation that some of the rules will overlap what will result in the troubleshooting nightmare.

Some Recommended Practices for NSG use:
⦁	Sometimes less is more — you don’t need to create NSG per subnet or per NIC, group your resources together, design your network properly so you can create fewer NSG’s which can be assigned across similar resources
⦁	What comes first — For both inbound and outbound traffic a NSG that is applied to the NIC takes priority over a NSG applied to the subnet. Try to avoid assigning NSGs to the NICs unless it is last option, it is easier to control rules on the subnet level.
⦁	Lower is better — the order of NSG rules is very important, NSG rules are applied in a prioritised order between 100 & 4,096, with each new rule being sequentially added. Rules evaluation starts from the lowest to highest priority numbers
⦁	A bad plan is better than none at all — plan your deployment ahead, analyse subnets and required port scopes, with foundations arranged properly it will be much easier to manage your NSGs later
⦁	Call a spade a spade — make sure to implement uniform and readable naming convention for your rules so they can be easily identified
NSG Flow Logs
It’s vital to monitor, manage, and know your own network so that you can protect and optimize it. You need to know the current state of the network, who’s connecting, and where users are connecting from. You also need to know which ports are open to the internet, what network behavior is expected, what network behavior is irregular, and when sudden rises in traffic happen.
Network security group flow logging is a feature of Azure Network Watcher that allows you to log information about IP traffic flowing through a network security group.
Important: Again, please plan ahead, NSG flow logs can generate huge amount of data which may result in some increase in the subscription cost

What is ASG
Application Security Group (ASG), is a networking feature that allows you to group Azure virtual machines (VMs) based on the application to which they belong. ASGs enable network security group (NSG) policies to be defined using logical application groupings rather than individual VM IP addresses. This simplifies network security rule management, especially when multiple VMs belong to the same application or service. Application Security Groups are especially useful in complicated and distributed application architectures where VMs must safely communicate across network boundaries. You can use ASGs to ease the maintenance of network security rules, improve security, and simplify application deployment in Azure.
ASG Benefits
Application Security Groups (ASGs) offer several advantages for managing network security in Azure, including:
⦁	Consistent Security Policies: With ASGs, you can ensure all VMs within a group follow the same security policies.
⦁	Granular Control: Create detailed network security policies based on workloads, applications, or environments. ASGs facilitate network segmentation to contain breaches.
⦁	Scalability: ASGs automatically adjust to accommodate changes in VM scale, eliminating the need for additional configuration.
