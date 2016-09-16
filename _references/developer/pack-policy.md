---
title: Pack policy
id: pack-policy
---

Policies can also be specified as part of the pack definition. The enables policy evaluation on the platform instance components
created out of the packs. The platforms with violated policies can then be fixed to avoid issues further down the application lifecycle.

Following are few examples of pack based policies.

~~~ruby
policy "env-profile",
       :description => 'custom pack policy for env-profile',
       :query => 'ciClassName:manifest.Environment AND _missing_:ciAttributes.profile'

policy "compute-ostype",
       :description => 'custom pack policy for compute-ostype',
       :query => 'ciClassName:(catalog.*Compute manifest.*Compute bom.*Compute) AND NOT ciAttributes.ostype:("centos-6.5" OR "centos-6.6" OR "redhat-6.5" OR "redhat-6.6" OR "default-cloud")'

policy "env-automation",
       :description => 'custom pack policy for env-automation',
       :query => 'ciClassName:manifest.Environment AND ciAttributes.profile:(PROD EBF STAGING) AND NOT (ciAttributes.autorepair:true AND ciAttributes.autoreplace:true)'
~~~ 
 