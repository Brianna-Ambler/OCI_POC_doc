# Introduction
This workshop will simulate typical dataflow for a retail application from  source to target where it is consumed for business analytics. It will be a  use case where executives of retail application send targeted marketing to prospective customers.
These customers are determined by analytical queries on location and relationship to prior customers.
Purchase transactions (relational data) aggregated to determine their top 10 customers (analytics function), finds those customer’s friends (graph data), filters the friends based on similar location (spatial data).

## Introduction to Technologies ##

###Oracle 19c Database:###
Oracle Cloud Infrastructure offers single-node DB systems on either bare metal or virtual machines, and 2-node RAC DB systems on virtual machines. We will be using Oracle Database 19c instance on a Virtual Machine
For more about Virtual DB systems, click [here](https://docs.cloud.oracle.com/en-us/iaas/Content/Database/Concepts/overview.htm).

###Dataflow:###
Oracle Cloud Infrastructure (OCI) Data Flow is a fully managed Apache Spark service to perform processing tasks on extremely large data sets without infrastructure to deploy or manage. This enables rapid application delivery because developers can focus on app development, not infrastructure management.
For more about OCI Dataflow, click [here](https://www.oracle.com/big-data/data-flow/)

###Oracle Resource Manager:###
Resource Manager is an Oracle Cloud Infrastructure service that allows you to automate the process of provisioning your Oracle Cloud Infrastructure resources. Using Terraform, Resource Manager helps you install, configure, and manage resources through the "infrastructure-as-code" model.

For more about Resource Manager, click [here](https://docs.oracle.com/en-us/iaas/Content/ResourceManager/Concepts/resourcemanager.htm)
### SQL Developer: ###
Oracle SQL Developer is a free, integrated development environment that simplifies the development and management of Oracle Database in both traditional and Cloud deployments. SQL Developer offers complete end-to-end development of your PL/SQL applications, a worksheet for running queries and scripts, a DBA console for managing the database, a reports interface, a complete data modeling solution, and a migration platform for moving your 3rd party databases to Oracle.



For more about SQL Devvloper, click [here](https://www.oracle.com/database/technologies/appdev/sqldeveloper-landing.html).

## Workshop Objectives ##
- Access a DB System
- Create Dataflow jobs using Oracle Resource Manager
- Create and load data in Graph database
- Execute queries on database

Estimated Workshop Time:  4 hours

## Acknowledgements

- **Authors/Contributors** - Sandeep Keni, Hasan Dange
- **Last Updated By/Date** -
