---
title: Metrics Collection
id: metrics-collection
---

# Overview
OneOps uses *Logstash* and *Logstash-Forwarder* to collect
 performance metrics (like CPU, Memory, jvm metrics)

# Logstash

* Log/Event processing engine written in jruby and runs as a jvm application
* The log lines flow through 3 different stages:
  * Input
  * Filters
  * and Outputs
* There are many standard inputs, filters and output plugins available
* We have custom output plugin for calling using collector java code.
* Logstash needs a simple config file in json format specify input, filters and outputs
* Logstash  coexist on collector machine.

# Logstash-Forwarder

* It is a “go” binary which tails log files and forwards the lines to downstream Logstash servers over “lumberjack” protocol
* Main goals of this tool are:
  * Minimize resource usage where possible (CPU, memory, network).
  * Secure transmission of logs.
  * Easy to deploy with minimal moving parts.
* Runs on user VMs.
* Gets installed as part of compute cookbook

# How it all Works Together

![](../../assets/local/images/logstash-logstash.png)
