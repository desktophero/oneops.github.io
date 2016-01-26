---
title: Platform Management Pack
id: platform-management-pack
---

A platform is added to the system by creating a Platform Management Pack (`Pack`) file and loading it into the [CMS](../howto/#cms-sync). A Pack is a Ruby DSL file that models a platform. It exists in the packer directory structure.

The file contains:

* Component Resources: Named resources with the type (cookbook attribute) and the [Component Class](../key-concepts/#component-class) name
* [Relationships/dependencies](../key-concepts/#relationships) with flexing/scaling attributes
* [Metrics/Thresholds](../references/#monitor) (optional) 

A Pack can extend another Pack, which keeps the model clean and manageable. Packs are versioned to match a set of recipes.

For instructions on how to add a new platform, refer to [Add a Platform.](../howto/#add-a-platform).

