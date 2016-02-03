---
title: "Testing and Debugging"
id: "testing-and-debugging"
---

# Testing
* Set up an developer instance for you and your team.
* If you have  developed a new pack, you should test both for
  * Single Mode
  * Redundant Mode
  * Test for both optional and mandator components.
  * Test all operation actions effected.
* If you are modifying metadata, deleting an attribute can have  
implications especially in production environments.

# Debugging
* For detailed debugging to show in the logs, turn on *debug* flag
on the environment page to see detailed logging.
* For debugging, you can capture the ~~~chef-solo~~~ command and execute on remote vm or inductor vm.
