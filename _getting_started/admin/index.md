---
title: "Getting Started"
id: "getting-started"
---

To get started with OneOps installation , you can start with

1. Getting Started with OneOps public [AMI](#geting-started-with-oneops-public-ami)
2. Use [Vagrant](#installing-vagrant-image)

# Getting Started with OneOps public AMI

If you have a AWS account you can bring up a basic version of OneOps using public AMI. (Right now available in US east region). This image have some basic configuration already in place.


## Find OneOps public image

On your EC2 Dashboard make sure you have selected N.Virginia region
In IMAGES/AMIs tab, make sure you select "Public images" in the drop down and search for OneOps. The image with name OneOps-basic-preconf-v1.* is the right one (pick the latest version).

## Launch your instance
1. Select the OneOps AMI and hit Launch. </br>
2. On the "Instance Type" tab make sure you select m4.large or bigger, OneOps needs at least 8GB of RAM. </br>
3. On the "Instance Details" is usually ap to you but if you want to have a public ip enable Auto-assign Public IP. </br>
4. On the "Add storage tab" make sure you have 2 volumes. </br>
Name you instance </br>
5. On the "Security group" add rule to open port 3000. OneOps UI is an rails app and runs on this image in development mode so you can check logs and see what's going on under the hood.</br>
6. Review and launch. When instance comes up, in your browser hit url http://your-public-ip:300
</br>
If login page comes up you are ready to go, login as oneops/oneops
If not - check the [troubleshooting](#troubleshooting) section.

## Login into OneOps
The AMI have preregistered user *oneops/oneops* within organization "OneOps". Also we have created simple assembly called **SimpleApache**. You can start browsing around. </br>
But if you want to deploy this test assembly to EC2 cloud you need to provide your credentials

##	Configure Cloud

In the left nav click on Clouds - you will be taken to the list of clouds configured in the system.</br>

![EC2 home page ](../../assets/local/images/GettingStartedEC2HomePage.png)

The one we have created for you is aws-east-1. Click on it and go to the cloud detail page.
On the right hand side you will see the list of services this cloud provides. </br>

![EC2Cloud Home ](../../assets/local/images/GettingStartedEC2Cloud.png)


For each one of them you will have to provide your access key and secret key.
* Make sure this user has appropriate permissions to manage cloud services (EC2,route53 as the case may be)

Yes you will have to do it for each one of them which is pain, but what if you want to use services from different providers :-)



![](../../assets/local/images/GettingStartedEC2Service.png)

## Deploy Simple Assembly

We have pre-created simple assembly named *SimpleApache*. This assembly have just one Apache platform with all out of the box default configuration values. You can examine it by clicking Assemblies (left nav) and then on SimpleApache. This will take you to the Assembly summary page which will have pretty much nothing since no activity was performed on this assembly. Click on "Design" (left nav) and you will get to the Assembly Design page where you can review platforms your assembly composed of (just one in this case) and if you click on the platform you will get onto "Platform Design Page". Just browse around.
Next step is to try to deploy this simple assembly: </br>

Go to "transition" page (left nav). You will see there is one environment already pre-created - "test-env", click on it and get onto Environment detail page. There is same one platform here as it was in design, but it's in disabled state, in order to deploy it you need to enable it. In little drop down menu you can do this.

![](../../assets/local/images/GettingStartedEC2EnablePlatform.png)

Next step commit your changes and deploy:

![](../../assets/local/images/GettingStartedEC2CommitAndDeploy.png)

The system will generate the deployment plan with steps that will be executed. Review them and hit deploy:

![](../../assets/local/images/GettingStartedEC2Deploy.png)

While deployment is in progress you can click on the steps to expand to work orders (one step can have multiple work orders). And there you can click on the log link to see what's going under the hood.Once deployment is complete you can go to operations page and examine what you have there. Also check your ec2 dashboard to see the result.

See Also

 * [Trouble connecting to port 3000](../testing#ui-does-not-come-up-on-aws-image)
 * [Deployment fails ](../testing#deployment-fails-on-aws-image)
 * We can help :<span class="button icon-slack"><a href="{{ site.slack_url }}" target="_blank">{{ site.slack_channel }}</a></span>


To get your first instance of OneOps working, a Vagrant [setup](
https://github.com/oneops/setup) is provided.

# Installing Vagrant Image
## Check Out the Vagrant Project

```bash
$ git clone https://github.com/oneops/setup
$ cd setup/vagrant
$ vagrant up
```

Once Jenkins starts, you can monitor the building process on : <a href="http://localhost:3003" target="_blank">http://localhost:3003</a>

![](../../assets/local/images/vagrant-build-progress.png)

# Setup and Configuration

Once the build is complete, the following message appears:

```bash
==> default: Done with admin
==> default: OneOps should be up on http://localhost:3000
==> default: Configure your port forwarding and shut down iptables service (or configure it) if needed
==> default: All done at : 15:28:54
```
# Set up Vagrant Inductor
Refer [Install](https://github.com/oneops/setup#install)

To continue the setup, connect to <a href="http://localhost:9090" target="_blank">http://localhost:9090.</a>

Create your first user by going through the registration process.

![](../../assets/local/images/admin-first-registration.png)

After the registration process is complete, log in with the new user you created.


You are now in OneOps.

## Create Cloud Provider

Before you can deploy and manage applications using OneOps, you have to add a Cloud Provider.

## Create an Organization

![](../../assets/local/images/admin-first-screen.png)

Create the first organization.

![](../../assets/local/images/admin-create-organization.png)

## Add a Cloud


To add a cloud, refer to the following:

![](../../assets/local/images/admin-add-cloud.png)
![](../../assets/local/images/admin-create-cloud.png)
![](../../assets/local/images/admin-cloud-created.png)



# Before You Begin

Before you begin, read the following documentation. It is the most essential information you need to start well.

* **[Overview:](../)** OneOps business-level description of main benefits versus alternative solutions
* **[Key Concepts:](../key-concepts)** Conceptual description and diagram of how OneOps works
* **[Tools:](../tools)** List of supporting tools and services that can be used with OneOps
* **[Getting Started:](../getting-started)** How to start using OneOps (this section)
* **[Best Practices:](../best-practices)** How you should use OneOps for best results

# What You Will Need When You Work

Refer to the following documentation as you work.

* **[Typical Usage Scenarios:](../typical-scenarios)** How components work together to enable commonly implemented scenarios
* **[References:](../references)** Detailed code usage descriptions with code snippets
* **[Testing & Debugging:](../testing)** Strategic overview description of how to test and debug OneOps
* **[Updates:](../updates)** Release and patch announcements as well as articles of interest to OneOps users
* **[Contribution:](../contribution)** How to provide feedback, report issues, contribute to development, or contact us
