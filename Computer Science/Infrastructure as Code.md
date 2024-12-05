Infrastructure as code is the paradigm of managing system configurations through the use of a [[Programming Languages#Domain Specific Language|programming language]] rather than interactive tools. This makes deployment itself a task which can be handled programatically. The prominent use case for this is on [[Distributed Computing|bare-metal servers]], [[Virtualisation|virtual machines]], or in [[Cloud Computing|cloud computing]].

Infrastructure as code can be conducted through the use of a controller which determines how the infrastructure of a server is setup. This is usually done through *pushes* which send configurations to devices, or *pulls* which receive configurations. This code commonly follows a [[Programming Paradigms#Declarative|declarative]], or [[Programming Paradigms#Procedural|procedural]] structure.

# Ansible
Ansible is an automation engine that allows for the creation and setup of 

Ansible uses an **inventory file** to communicate with existing servers. This matches 