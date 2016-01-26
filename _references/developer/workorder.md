---
title: WorkOrder
id: workorder
---

A WorkOrder is a collection of managed objects that are used to add, update or delete a component.

[ActionOrders]({{site.contexts.admin}}key-concepts/#actionorders) are actions such as start, stop, restart, status, repair, etc. 

A WorkOrder is sent from the controller to a message queue by zone. The inductor consumes from the queue and executes the chef-solo command using the data from the WorkOrder. It runs locally or remotely via SSH using the `ManagedVia` relationship.

When the inductor is finished with a `WorkOrder`, it posts a `WorkorderResponse` event to the controller with a resultCi that updates the CMS.

```http
chef-solo -c /home/oneops/cookbooks/chef.rb -j /opt/oneops/workorder/<some workorder>.json
```

<br/>
Chef-solo uses the `run_list` in the WorkOrder to determine what code to run.

The following is a sample compute:add WorkOrder json file:

```json
{
  "mgmt_domain": "qa.oneops.com",
  "customer_domain": "s3rss.test-php-mysql.oneops.com",
  "run_list": [
    "recipe[compute::add]",
    "recipe[shared::monitor]"
  ],
  "workorder": {
    "rfcCi": {
      "ciAttributes": {
        "ostype": "ubuntu-12.04",
        "hosts": "{}",
        "image_id": "",
        "size": "S"
      },
      "ciBaseAttributes": {},
      "ciAttrProps": {},
      "rfcId": 456467,
      "releaseId": 456466,
      "ciId": 1578346,
      "nsPath": "/oneops/test-php-mysql/s3rss/bom/db/1",
      "ciClassName": "bom.Compute",
      "ciName": "db-compute-1189982-1",
      "ciGoid": "1578191-1082-1578346",
      "rfcAction": "remote",
      "execOrder": 1,
      "comments": "",
      "isActiveInRelease": true,
      "created": "Nov 14, 2012 1:53:31 AM"
    },
    "zone": {
      "ciAttributes": {
        "authkey": "",
        "subnet": ""
      },
      "ciId": 23405,
      "ciName": "rackspace.us-south",
      "ciClassName": "account.provider.Zone",
      "nsPath": "/public/packer/providers/rackspace",
      "ciGoid": "23398-1476-23405",
      "comments": "",
      "ciState": "default",
      "lastAppliedRfcId": 0,
      "created": "Mar 5, 2012 11:28:11 PM",
      "updated": "Sep 4, 2012 5:26:19 PM"
    },
    "token": {
      "ciAttributes": {
        "rackspace_username": "na",
        "rackspace_api_key": "na"
      },
      "ciId": 1189976,
      "ciName": "rackspace",
      "ciClassName": "account.provider.rackspace.Token",
      "nsPath": "/oneops/providers/rackspace",
      "ciGoid": "1189975-1398-1189976",
      "ciState": "default",
      "lastAppliedRfcId": 0,
      "createdBy": "qa@oneops.com",
      "updatedBy": "qa@oneops.com",
      "created": "Sep 20, 2012 5:33:12 AM",
      "updated": "Nov 13, 2012 4:15:50 PM"
    },
    "resultCi": {
      "ciAttributes": {
        "public_ip": "50.56.174.231",
        "private_ip": "10.180.10.13",
        "private_dns": "10.180.10.13",
        "public_dns": "50.56.174.231",
        "instance_id": "93d88570-c447-44a9-86ec-c6846b1520c3",
        "ostype": "ubuntu-12.04",
        "hosts": "{}",
        "image_id": "",
        "size": "S"
      },
      "ciId": 1578346,
      "ciClassName": "bom.Compute",
      "lastAppliedRfcId": 456467
    },
    "box": {
      "ciAttributes": {
        "source": "packer",
        "is_active": "true",
        "description": "",
        "major_version": "1",
        "pack": "mysql",
        "version": "0.4",
        "availability": "single"
      },
      "ciId": 1577845,
      "ciName": "db",
      "ciClassName": "manifest.Platform",
      "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
      "ciGoid": "1577844-1316-1577845",
      "ciState": "default",
      "lastAppliedRfcId": 455748,
      "createdBy": "qa@oneops.com",
      "created": "Nov 14, 2012 1:03:28 AM",
      "updated": "Nov 14, 2012 1:03:28 AM"
    },
    "payLoad": {
      "RealizedAs": [
        {
          "ciAttributes": {
            "ostype": "ubuntu-12.04",
            "hosts": "{}",
            "image_id": "",
            "size": "S"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577854,
          "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
          "ciClassName": "manifest.Compute",
          "ciName": "db-compute",
          "ciGoid": "1577844-1081-1577854",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 455787,
          "comments": "",
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:28 AM",
          "updated": "Nov 14, 2012 1:03:28 AM"
        }
      ],
      "Environment": [
        {
          "ciAttributes": {
            "monitoring": "true",
            "autorepair": "false",
            "description": "",
            "dpmtdelay": "60",
            "subdomain": "s3rss.test-php-mysql.oneops",
            "domain": "oneops.com",
            "codpmt": "false",
            "autoscale": "false",
            "availability": "single"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577829,
          "nsPath": "/oneops/test-php-mysql",
          "ciClassName": "manifest.Environment",
          "ciName": "s3rss",
          "ciGoid": "635730-1134-1577829",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 0,
          "comments": "",
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:07 AM",
          "updated": "Nov 14, 2012 1:03:07 AM"
        }
      ],
      "region": [
        {
          "ciAttributes": {
            "imagemap32": "{}",
            "imagemap64": "{"centos-6.3":"c195ef3b-9195-4474-b6f7-16e5bd86acd0",%5Cn       "ubuntu-11.04":"8bf22129-8483-462b-a020-1754ec822770",%5Cn       "ubuntu-11.10":"3afe97b2-26dc-49c5-a2cc-a2fc8d80c001",%5Cn       "ubuntu-12.04":"5cebb13a-f783-4f8c-8058-c4182c724ccd",%5Cn       "fedora-16":"bca91446-e60e-42e7-9e39-0582e7e20fb9",%5Cn       "fedora-17":"d42f821e-c2d1-4796-9f07-af5ed7912d0e"}",
            "sizemap": "{"XS":"3","XL":"7","S":"4","M":"5","L":"6"}",
            "archmap": "{"3":"64","4":"64","5":"64","6":"64","7":"64"}"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 23399,
          "nsPath": "/public/packer/providers/rackspace",
          "ciClassName": "account.provider.Region",
          "ciName": "rackspace.us-south",
          "ciGoid": "23398-1360-23399",
          "execOrder": 0,
          "lastAppliedRfcId": 0,
          "comments": "",
          "isActiveInRelease": false,
          "created": "Mar 5, 2012 11:28:10 PM",
          "updated": "Nov 5, 2012 3:24:14 PM"
        }
      ],
      "Entrypoint": [
        {
          "ciAttributes": {
            "source": "packer",
            "is_active": "true",
            "description": "",
            "major_version": "1",
            "pack": "mysql",
            "availability": "single",
            "version": "0.4"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577845,
          "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
          "ciClassName": "manifest.Platform",
          "ciName": "db",
          "ciGoid": "1577844-1316-1577845",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 455748,
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:28 AM",
          "updated": "Nov 14, 2012 1:03:28 AM"
        }
      ],
      "Organization": [
        {
          "ciAttributes": {
            "dns_secret": "na",
            "domain": "oneops.com",
            "dns_key": "na"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 476012,
          "nsPath": "/",
          "ciClassName": "account.Organization",
          "ciName": "oneops",
          "ciGoid": "100-1284-476012",
          "updatedBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 0,
          "isActiveInRelease": false,
          "created": "Jun 11, 2012 11:16:28 PM",
          "updated": "Oct 19, 2012 1:28:55 AM"
        }
      ],
      "Assembly": [
        {
          "ciAttributes": {
            "description": "main"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 635728,
          "nsPath": "/oneops",
          "ciClassName": "account.Assembly",
          "ciName": "test-php-mysql",
          "ciGoid": "476013-1029-635728",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 0,
          "isActiveInRelease": false,
          "created": "Jul 3, 2012 4:57:26 PM",
          "updated": "Jul 3, 2012 4:57:26 PM"
        }
      ],
      "WatchedBy": [
        {
          "ciAttributes": {
            "thresholds": "{}",
            "cmd": "check_local_load!5.0,4.0,3.0!10.0,6.0,4.0",
            "duration": "5",
            "metrics": "{"load1":{"unit":"","description":"Load 1min Average","display":true},"load5":{"unit":"","description":"Load 5min Average","display":true},"load15":{"unit":"","description":"Load 15min Average","display":true}}",
            "heartbeat": "true",
            "description": "Load",
            "chart": "{"min":0}",
            "cmd_line": "/opt/nagios/libexec/check_load -w $ARG1$ -c $ARG2$"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577869,
          "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
          "ciClassName": "manifest.Monitor",
          "ciName": "db-compute-load",
          "ciGoid": "1577844-1243-1577869",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 455866,
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:28 AM",
          "updated": "Nov 14, 2012 1:03:28 AM"
        },
        {
          "ciAttributes": {
            "thresholds": "{"LowDiskInode":{"trigger":{"operator":"%5Cu003e","value":90,"numocc":1,"duration":5},"metric":"inode_used","stat":"avg","reset":{"operator":"%5Cu003c","value":90,"numocc":1,"duration":5},"bucket":"5m","state":"notify"},"LowDiskSpace":{"trigger":{"operator":"%5Cu003e","value":90,"numocc":1,"duration":5},"metric":"space_used","stat":"avg","reset":{"operator":"%5Cu003c","value":90,"numocc":1,"duration":5},"bucket":"5m","state":"notify"}}",
            "cmd": "check_disk_use!/",
            "duration": "3",
            "metrics": "{"space_used":{"unit":"%","description":"Disk Space Percent Used","display":true},"inode_used":{"unit":"%","description":"Disk Inode Percent Used","display":true}}",
            "heartbeat": "false",
            "description": "Disk",
            "chart": "{"unit":"%","min":0}",
            "cmd_line": "/opt/nagios/libexec/check_disk_use.sh $ARG1$"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577871,
          "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
          "ciClassName": "manifest.Monitor",
          "ciName": "db-compute-disk",
          "ciGoid": "1577844-1243-1577871",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 455876,
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:28 AM",
          "updated": "Nov 14, 2012 1:03:28 AM"
        },
        {
          "ciAttributes": {
            "thresholds": "{"HighCpuPeak":{"trigger":{"operator":"%5Cu003c%5Cu003d","value":10,"numocc":1,"duration":5},"metric":"CpuIdle","stat":"avg","reset":{"operator":"%5Cu003e","value":20,"numocc":1,"duration":5},"bucket":"5m","state":"notify"},"HighCpuUtil":{"trigger":{"operator":"%5Cu003c%5Cu003d","value":20,"numocc":1,"duration":60},"metric":"CpuIdle","stat":"avg","reset":{"operator":"%5Cu003e","value":30,"numocc":1,"duration":60},"bucket":"1h","state":"notify"}}",
            "cmd": "check_local_cpu!10!5",
            "duration": "3",
            "metrics": "{"CpuIdle":{"unit":"%","description":"Idle %","display":false},"CpuSteal":{"unit":"%","description":"Steal %","display":true},"CpuUser":{"unit":"%","description":"User %","display":true},"CpuIowait":{"unit":"%","description":"IO Wait %","display":true},"CpuNice":{"unit":"%","description":"Nice %","display":true},"CpuSystem":{"unit":"%","description":"System %","display":true}}",
            "heartbeat": "false",
            "description": "CPU",
            "chart": "{"unit":"Percent","max":100,"min":0}",
            "cmd_line": "/opt/nagios/libexec/check_cpu.sh $ARG1$ $ARG2$"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577873,
          "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
          "ciClassName": "manifest.Monitor",
          "ciName": "db-compute-cpu",
          "ciGoid": "1577844-1243-1577873",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 455886,
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:28 AM",
          "updated": "Nov 14, 2012 1:03:28 AM"
        },
        {
          "ciAttributes": {
            "thresholds": "{}",
            "cmd": "check_local_mem!90!95",
            "duration": "3",
            "metrics": "{"used":{"unit":"KB","description":"Used Memory","display":true},"total":{"unit":"KB","description":"Total Memory","display":true},"free":{"unit":"KB","description":"Free Memory","display":true},"caches":{"unit":"KB","description":"Cache Memory","display":true}}",
            "heartbeat": "false",
            "description": "Memory",
            "chart": "{"unit":"KB","min":0}",
            "cmd_line": "/opt/nagios/libexec/check_mem.pl -Cu -w $ARG1$ -c $ARG2$"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 1577875,
          "nsPath": "/oneops/test-php-mysql/s3rss/manifest/db/1",
          "ciClassName": "manifest.Monitor",
          "ciName": "db-compute-mem",
          "ciGoid": "1577844-1243-1577875",
          "createdBy": "qa@oneops.com",
          "execOrder": 0,
          "lastAppliedRfcId": 455896,
          "isActiveInRelease": false,
          "created": "Nov 14, 2012 1:03:28 AM",
          "updated": "Nov 14, 2012 1:03:28 AM"
        }
      ],
      "RequiresComputes": [
        {
          "ciAttributes": {
            "ostype": "ubuntu-12.04",
            "hosts": "{}",
            "image_id": "",
            "size": "S"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 456467,
          "releaseId": 456466,
          "ciId": 1578346,
          "nsPath": "/oneops/test-php-mysql/s3rss/bom/db/1",
          "ciClassName": "bom.Compute",
          "ciName": "db-compute-1189982-1",
          "ciGoid": "1578191-1082-1578346",
          "rfcAction": "add",
          "createdBy": "qa@oneops.com",
          "rfcCreatedBy": "qa@oneops.com",
          "execOrder": 1,
          "comments": "",
          "isActiveInRelease": true,
          "rfcCreated": "Nov 14, 2012 1:53:31 AM",
          "rfcUpdated": "Nov 14, 2012 1:53:31 AM",
          "created": "Nov 14, 2012 1:53:31 AM",
          "updated": "Nov 14, 2012 1:53:31 AM"
        }
      ],
      "ManagedVia": [
        {
          "ciAttributes": {
            "public_ip": "50.56.174.231"
          },
          "ciBaseAttributes": {},
          "ciAttrProps": {},
          "rfcId": 0,
          "releaseId": 0,
          "ciId": 0,
          "execOrder": 0,
          "isActiveInRelease": false
        }
      ]
    },
    "dpmtRecordId": 456515,
    "deploymentId": 456514,
    "rfcId": 456467,
    "dpmtRecordState": "successful",
    "created": "Nov 14, 2012 1:53:37 AM"
  },
  "dns_domain": "oneops.com",
  "name": "db-compute-1189982-1",
  "global": {},
  "compute": {
    "ostype": "ubuntu-12.04",
    "hosts": "{}",
    "image_id": "",
    "size": "S"
  },
  "public_key": "na",
  "app_name": "compute"
}
```

# See Also

* [Architecture Diagram](../key-concepts/#oneops-system-architecture)

