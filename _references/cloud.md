---
title: "cloud"
id: "cloud"
---

### Primary and Secondary Clouds

To create an environment, it is necessary to select one or more primary clouds and optional secondary clouds.

* **Primary Cloud:** All primary clouds are enabled on GLB (global VIP), unless shutdown, and hence they receive all the traffic
* **Secondary Cloud:** All secondary clouds are disabled and do not receive requests from GLB

![](../assets/local/images/key-concepts-primary-and-secondary-clouds.png)

OneOps supports the selection of one or more primary or secondary clouds for any given environment. 
An existing environment cloud definition, whether primary or secondary, can be edited at any time.
