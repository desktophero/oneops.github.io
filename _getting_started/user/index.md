---
title: "Getting Started"
id: "getting-started"
---

>This getting started guide assumes that you have a **_running_ _OneOps_ _instance_**, if not refer to [initial set up][]

<div id="wizard" class="rounded">
  <div class="inner rounded">
      <ul class="steps">
        <li class="alert account alert-success">
            <span class="step-title alert-heading">Account</span>

            <ul class="tasks">
                <li class="task"> <a href="#create-cloud">create clouds</a></span></li>
                <li class="task"> <a href="#create-an-assembly">create assembly</a></span></li>

            </ul>
            <span class="step-number">1</span>
        </li>
        <li class="alert alert-info design">
            <span class="step-title alert-heading">Design</span>
            <ul class="tasks">
                  <li class="task"><a href="#create-a-platform">create platform</a></li>
                <li class="task"><a href="#commit-a-design">commit design</a></li>
            </ul>
            <span class="step-number">2</span>
        </li>
        <li class="alert alert-info transition">
            <span class="step-title alert-heading">Transition</span>
            <ul class="tasks">

                <li class="task"><a href="#create-an-environment">create environment</a></li>
                <li class="task"><a href="#deploy-an-application">deploy to cloud</a></li>
            </ul>
            <span class="step-number">3</span>
        </li>
        <li class="alert alert-info operate">
            <span class="step-title alert-heading">Operate</span>
            <ul class="tasks">
                <li class="task"><a href="#view-operations">view status</a></li>
                <li class="task"><a href="#control-environment">control environment</a></li>
            </ul>
            <span class="step-number">4</span>
        </li>
    </ul>
</div>
</div>

# Account

This section describes how to set up your account, organization, assemblies.

1. Login/Register in OneOps to access/create your Organization.
2. Not seeing your Organization? Lookup the Organization you are interested in. Ask Organization administrator to grant you access .
3. To create a new Organization? Follow these steps.

##Create Organization

  1. Click profile(your user name) on the left nav bar.
  2. Select **Organization** tab.
  2. Select new **Organization** from the right side.
  3. Enter Organization name and click save.
  4. This will bootstrap an Organization with reasonable defaults which can be changed later.


##Create Cloud
>Noramally administrator of the organization creates a cloud, it may require creating an [inductor][] or adding cloud to an exiting inductor.  

  1. Create [Organization](#create-organization) if one does not exist.
  2. Click **clouds** link on left nav bar .
  2. Click **Add Cloud**  

![Getting started OneOps]({{site.baseurl}}/assets/local/images/create-clouds-orgs.gif)
Next **Create Assembly**

## Create an Assembly

Assembly is workspace for you application. To create an assembly

1. Click **Assemblies** from left nav or top nav .
2. In the assemblies listing page click **New Assembly** on the right hand side
or towards the end of listing.
3. Enter assembly details, Click save. Next [Create a Platform](#create-a-platform)


To learn about additional Account activities for assemblies, teams, users and notifications refer to:

* [Teams in Organization](../howto/#create-a-team-in-an-organization)
  * [Add a User to a Team](../howto/#add-a-user-to-a-team)
* [Manage Assemblies](../howto/#manage-assemblies)
  * [Adding a Team to an Assembly](../howto/#add-a-team-to-an-assembly)
  * [Watch Notification](../howto/#watch-a-notification)
  * [Specify an Email Address or Distribution List for Notification](../howto/#specify-an-email-address-or-distribution-list-for-notifications)
  * [Create an Assembly -- Design an Application](../howto/#create-assemblies-to-design-applications)

# OneOps Design Phase
In the design phase, one can create [platforms][](building blocks) from existing available *packs*.
In this example, we will create simple application(Tomcat) which talks to back end database.

## Create a Platform

1. Click design(icon) from left nav or top nav or wizard.
2. Click **New Platform** , choose from existing packs in **pack name**
3. Modify any attributes of *component* to suit your application design.

## Commit a design
4. Click **review** to your changes, all changes are buffered in a *release* and are not applied unless you commit.
5. Once satisfied click **commit** to commit the changes . Next **[Create Environment](#create-an-environment)**

~~~
* Change attributes of component which are common across environments.
* Add optional components /attachments in design phase.
~~~
See also:

* [Platforms][]  
 * [Add a platform][]
  * [Add a component][]
 * [Platform Dependency][]
 * [Packs/Circuits][]
* [View Design Releases](../howto/#view-design-releases)

# Transition Phase
Transition is where you define environment specific attributes as needed. The dev or qa environments may differ in terms of *availability* , *resources* needed and can be defined at environment level.

## Create an Environment
1. Click environment(icon) from left nav or top nav or wizard.
2. Click **New Environment** .
3. Select availability mode for your environment either at platform.
4. Modify any attributes of *[components][]* which may differ from design.

For example *qa* environment compute size requirements may differ from **development/test** or **productiion** environment , in such scenario you may choose default compute size based on what matches most of the environment requirements.

Its not uncommon to choose **devleopment** environment compute size as default for design which allows you to create multiple test environments without changing design.

This helps in creating environments faster without changing too many attributes at design level. As a best practice try to have most used configuration in design. Also see [variables][]

**Lock** any environment specific  attributes to prevent the environment changes
to be  override from design pulls.

5. Click **review** and **commit and deploy** your changes. Next **[Deploy](#deploy-an-application)**.

See also

* [Environment][]
* [Upgrade an Application Version in an Environment](../howto/#upgrade-an-application-version-in-an-environment)
* [Environment Releases](../howto/#environment-releases)
* [Environment-profiles][]

##Deploy an Application
1. Click `commit and deploy` Review the **deployment plan** generated by OneOps.  
  1. Click on a *particular* step to know what change is going to be deployed.
2. Want to change plan, **discard** and no changes would be deployed.
3. If satisfied click **green Deploy**

 It can take few minutes to deploy the application to cloud infrastructure selected during environment creation.

 At this time One Ops is executing actual work orders on the cloud of your choice, **switching** clouds is then matter of adding clouds and  shutting down clouds which may not be needed.

See also

* [Multi Cloud deployment](../howto/#deploy-multiple-clouds-in-parallel)
* [Check Deployment Status](../howto/#view-deployment-status)
* [Deploy and Provision an Application and Environment for the First Time](../howto/#deploy-and-provision-an-application-and-environment-for-the-first-time)
* [Doing regular releases](../howto/#deploy-application-after-design-changes)
* [Common Deployment errors](../howto/)

#Operate Phase

The successful deployment will *create* actual instances of components(computes,tomcats) on to cloud(s) chosen. Once you have *running environment* you would need to operate the environment which typically involves

## View Operations
1. View the status of your overall application.
2. View notifications, alerts, filter instances based on their state.

## Control Environment
3. Perform operational activities on [components][] level, like restart of all tomcats.
Some of the commonly used operations but not limited to these
    1. Replace of compute in case of hardware failures.
    2. Restart of services.(tomcat, Cassandra, elastic search)
    3. Some of [attachments][] can be exposed as operations. Some of the
    popular one used are taking nodes out of traffic.
    4. Redeploy artifacts.
    5. Log Searches on volume components.

3. Control auto-repair / auto-scale.
4. Perform repairs at cloud level.

See also

* [Assess the Health of Applications, Platforms and Clouds](../howto/#assess-the-health-of-applications-platforms-and-clouds)
* [Operations Summary](../howto/#operations-summary)
* [Graphs](../references/#graph-colors)
* [Control Environment](../howto/#control-environment)


## Monitoring
* OneOps by default will send emails(default notification mechanism) if any of components are in unhealthy or notify state. see [Monitoring][]
* If auto-repair is enabled , OneOps will auto -repair the instance. The actions taken to recover an instance are prescribed by `repair recipe` of the component. For example , if Compute is alerting for missing *heartbeat* by default Computes repair action involves the following
  1. Check the ssh port  
  2. If not able to connect after timeout, it will attempt *reboot*.
  3. These might recover the compute, if not then
   auto-replace would be triggered.


# OneOps Documentation for Users

## Before You Start with OneOps

Before you start with OneOps, it is recommended that you read the following documentation. It is the most essential information you need to begin well.

* **[Overview:](../)** OneOps business-level description of main benefits versus alternative solutions
* **[Key Concepts:](../key-concepts)** Conceptual description and diagrams of how OneOps works
* **[Tools:](../tools)** List of supporting tools and services that can be used with OneOps
* **[Getting Started:](../getting-started)** How to start using OneOps (this section)
* **[Best Practices:](../best-practices)** How you should use OneOps for best results

## What You Will Need When You Work with OneOps

Refer to the following documentation as you work.

* **[Typical Usage Scenarios:](../typical-scenarios)** How components work together to enable commonly implemented scenarios  
* **[Reference:](../references)** Detailed code usage descriptions.
* **[How To:](../howto)** 'How To' instructions that solve a specific problem or achieve a specific solution
* **[Testing & Debugging:](../testing)** Strategic overview description of how to test and debug OneOps
* **[Updates:](../updates)** Release and patch announcements as well as articles of interest to OneOps users
* **[Contribution:](../contribution)** How to provide feedback, report issues, contribute to development, or contact us

[Account]:../howto/#set-up-your-user-account
[Add a component]:../howto/#add-specific-component-to-design
[Add a Platform]:../howto/#add-a-platform-to-a-design
[Assembly]:../key-concepts/#Assembly
[attachments]:../references/#attachments
[auto-scale]:../references#auto-scale
[Availability Modes]:../references/#availability-modes
[catalogs]:../recipe/#catalogs
[clouds]:../references/#cloud
[commit design]:../howto/#add-a-platform-to-a-design
[Components]:../key-concepts/#component
[create assembly]:../howto/#create-assemblies-to-design-applications
[create design]:../howto/#add-a-new-cloud
[create environment]:../howto/#create-an-environment
[create platform]:../howto/#add-a-platform-to-a-design
[deploy to cloud]:../howto/deploy-to-cloud
[Design]:../key-concepts/#design-in-oneops
[Detailed Environment]:../references/#environment
[Detailed Transition]:../references/#transition
[Environment-Profiles]:../references/#environment-profiles
[Environment]:../key-concepts/#environment
[initial set up]:{{site.baseurl}}/{{site.contexts.admin}}getting-started
[inductor]:{{site.baseurl}}/{{site.contexts.admin}}references#inductor
[Monitoring]:../references/#monitoring
[Operations]:../key-concepts/#operations-in-oneops
[Packs/Circuits]:../references/#platform-packs
[Platform Dependency]:../references/#platform-links-reference
[platforms]:../key-concepts/#platform
[Transition]:../key-concepts/#transition-in-oneops
[User]:{{site.contexts.developer}}key-concepts/#deployment-architecture-overview
[variables]:../references#variables
