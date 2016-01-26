---
title: "Azure"
id: "azure"
---

 Only Azure Resource Manager (ARM) is supported in OneOps.  
 Currently only Linux workloads are supported.  Windows will come at a later date.  
 
 If you are **not** using Express Routes, everything is dynamically created apart from the 4 pieces of information needed to communicate with Azure; Tenant Id, Subscription Id, Client Id, and Client Secret.  
 
 When you deploy into an Azure cloud, it will generate a Resource Group and Availability set in the first step of deployment.  
 The resource group and availability set will be named: `{org}-{assembly}-{platform}-{env}-{region}`  
 
 During creation of the computes the NIC's, OS disk, VNETs, Subnets, and public IPs will be created.  
 If you are using the Express Route option, a public ip, VNET and Subnet will not be created, instead it will use what was configured when the cloud service was setup.  
 
 After the compute is created the rest of the deployment is the same as it would be for the other cloud providers, except DNS, LB, and GDNS.  
 
 DNS is explained here: [Azure DNS]({{site.baseurl}}/{{site.contexts.user}}howto/#add-cname-in-azure-dns)  
 
 The Load Balancer has many parts.  
 Content coming shortly...
 
 Traffic Manager.  
 Content coming shortly...