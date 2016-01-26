---
title: Manually build from source
id: manually-build-from-source
---

To build project from source, follow the steps below.  If building on linux, there may be a few extra steps that may be needed, shown in the 'LINUX ONLY' notes below.  

## Install Ruby

```bash
# Install RVM
$ curl -sSL https://get.rvm.io | bash
$ source /home/vagrant/.rvm/scripts/rvm
# Install Ruby
$ rvm list known
$ rvm install ruby-1.9.3
# Make it default
$ rvm use --default ruby-1.9.3
$ ruby -v
ruby 1.9.3p547 (2014-05-14 revision 45962) [x86_64-darwin13.2.0]
```

## Install Chef

```bash
$ sudo gem install chef
```

[comment]: # (Is this required? $ sudo gem install knife) 

## Build oneops-admin-VERSION.gem

1. Build the 'cmsdal' project
  
    ```bash
$ git clone https://github.com/oneops/cmsdal
$ cd cmsdal
$ mvn install 
```
   
2. Build the 'oo-commons' project
  
    ```bash
$ git clone https://github.com/oneops/oo-commons
$ cd oo-commons
$ mvn install 
```
  
3. Build the 'daq' project
  
    ```bash
$ git clone https://github.com/oneops/daq
$ cd daq
$ mvn install 
```
  
4. Build the 'inductor' project
  
    ```bash
$ git clone https://github.com/oneops/inductor
$ cd inductor
$ mvn clean package
$ gem build inductor.gemspec
```
  
5. Build and install the OneOps Admin Circuit CLI
  
    ```bash
$ git clone https://github.com/oneops/oneops-admin
$ cd oneops-admin
$ mkdir target
$ cp ../inductor/target/inductor-*.jar target
$ gem build oneops-admin.gemspec
$ sudo gem install oneops-admin-*.gem
# To see the circuit help
$ circuit --help
```
  
    ```bash
# LINUX ONLY:
Install Ruby 1.9 dependencies:
$ gem install net-ssh -v 2.9.2
$ gem install mime-types -v 2.6.2
```
  
6. Get the OneOps Circuit source code.  Fork the repo and create a local clone of the forked repo.
  
    ```bash
$ git clone https://github.com/oneops/circuit-oneops-1
$ cd circuit-oneops-1
$ sudo gem install bundler
$ bundle install
```
   
    ```bash
# LINUX ONLY :
$ gem install bundler
$ gem install fog -v 1.20.0
$ bundle install
# linux :  sudo apt-get install libxslt-dev libxml2-dev
$ gem install nokogiri -v '1.5.11'
```  
  