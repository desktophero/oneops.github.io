---
title: "Testing and Debugging"
id: "testing-and-debugging"
---
As an admin become familiar with OneOps architecture

# Testing
* Build a *test* environment where you can test any new OneOps code changes and also validate any or new *pack* changes your organization might do.

# Debugging

## UI not coming up
  * Make sure the **apache** is up if running *display* in apache.
  * Run `nc -v host port` to see if the ports are not blocked. Do this for any of the  services.

## Deployments failing
  * Check if all consumers can connect to messaging bus.
  * All the oneops webapps( adapter,transistor) expose health check /rest/<context>/ecv/status.. so check if all web contexts are up.

## Inductor not coming up
* Make sure the *auth-key* is same which you used for setiing up the cloud.
