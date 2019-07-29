# How to: Create and Process Replication
Replication links Data Sets to particular Receiver and specifies what kind of data should be replicated. It is also possible to set up additional filters which will be applied during replication processing.

Replications can be found under **MDMS / Replications**.
Following fields are available in Replication header:
1.	**No.**  
Replication unique identifier
2.	**Description**  
Replication description
3.	**Receiver No.**  
No. of Receiver
4.	**Last Run Date and Time**  
Date and time of last successful replication
5.	**Status**  
Read-only field, contains Replication status. Status may be either Open or Released and can be adjusted using **Functions / Release** and **Functions/Reopen** actions

Following fields are available in Replication lines:
1.	**Data Set No.**  
No. of replicated Data Set
2.	**Description**  
Description of replicated Data Set

### Replication filters
Using Line / Show Filters action it is possible to specify additional filters that will be applied to data set records while processing replication.
Following fields are available:
1.	**Data Set Line No.**  
Line No. of Data Set being replicated
2.	**Data Set Line Code**  
Line Code of Data Set being replicated, filled in automatically as soon as Data Set Line No. is entered
3.	**Field No.**  
Field No. that filter will be applied against
4.	**Field Caption**  
Field caption, filled in automatically as soon as Field No. is entered
5.	**Value**  
Desired filter value

*NOTE: Please remember that Value is text-based field. If you want to set up a filter against option-type field, you need to ensure that filter value is correct.*
### Releasing/Reopening
After all necessary setup has been performed, it is necessary to mark Replication card as completed using **Functions / Release** action which will change its status to Released. Replication has to be released prior to running. If user wants to make any further adjustments to previously released Replication, it is necessary to reopen it first using **Functions / Reopen** action.
## Running replication

[Back](master-data-management-system-mdms.md)