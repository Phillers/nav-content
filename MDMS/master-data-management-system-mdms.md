# Master Data Management System (MDMS)

## Introduction

Master Data Management System (abbrev. MDMS) is a module that allows users to set up any set of data within MS Dynamics NAV database and replicate it to another NAV database to ensure data consistency.

Users are allowed to set up any number of Receivers, which are target companies, to which data will be replicated.

Structure of data replicated can be set up as Data Sets.

Users can use any number of created Data Sets and set them up to be replicated to particular Receiver, using Replication card. Replication can be either Full or Incremental; while processing Incremental replication, only data changed from the last Replication will be exported.

Module is particularly useful when company wants to create & maintain certain NAV cards (e.g. items, BOMs, vendors) in one company – called “master” company - and afterwards synchronize it with subsidiaries (“receiver” companies).

Module uses SOAP Web Services as a data transport layer.

## Content

1. [How to: Set up MDMS](how-set-mdms.md)
2. [How to: Create a Data Set](how-create-data-set.md)
3. [How to: Create and Process Replication](how-create-process-replication.md)