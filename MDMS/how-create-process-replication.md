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
While running replication, system first checks whether all Data Sets included in current replication are released and displays an error message if otherwise. Also, replication itself has to be released as well.
After successful replication, Record Synchronization Entries are created. Also, Last Run Date and Time field is updated on Replication card.
### Manual
User can run replication manually, from **Replication Card** or **Replication List**, using **Run (Full)** or **Run (Incremental)** functions.
*NOTE: It is possible to select multiple Replications on the list and run them altogether.*
### Automatic (using Job Queue)
It is possible to set up replication to be run automatically using Dynamics NAV Job Queue module.
It is necessary to set up **Codeunit no. 20020699 Run Replication (MDMS)** as Object ID to Run.
In Parameter String, following structure has to be followed:  
`<Replication No.>,<Replication Type>`  
Where:
-	Replication No. – contains Replication No. to be run;
-	Replication Type – specifies replication type, two possible values are: “FULL” and “INCREMENTAL”.  

Example Parameter String values are:
-	R0001,INCREMENTAL
-	R0025,FULL

Should Parameter String be invalid, Job Queue will fail with appropriate error message.
### Full vs Incremental
Each replication can be run in one of two modes: Full or Incremental. 

Full replication loops through all the records from Data Set, including filters set up on Replication line (if any). In case no filters has been set up, all records will be exported every time replication is run.

Incremental replication includes only data that has changed recently (since Last Run Date and Time as specified on Replication card). For each record that would normally be included as for Full replication, it performs additional check (using internal change log functionality) to see whether record should be exported.

*NOTE: Only top-level changes are recognized.*

Every successful replication run updates Last Run Date and Time field on Replication card.
### Replication Tracking Entries
Upon releasing Replication, a message may appear. 
When data set is included in released replication, all tables included are added to internal MDMS tracking log, which is utilized while processing incremental replications. However, any changes concerning tracking log are applied while opening a database and are persistent during user session.

*NOTE: It is therefore necessary that after each change, prior to processing a replication (especially incremental), user logs off and logs in back again.*
### Record Synchronization Entries
Every replication run creates Record Synchronization Entries for each processed record. They can be opened from Replication card by choosing **Navigate / Replication/ Record Synchronization Entries**.
Following fields are available:
1.	**Entry No.**  
Sequential No.
2.	**Date and Time**  
Date and time of Replication run
3.	**Status**  
Specifies if entry has been processed succesfully
4.	**Processed Date & Time and Processed By**  
Specifies when the entry has been processed and by which user
5.	**Error Text**  
Message thrown by error during processing
6.	**Old Record ID**  
Used in case of rename, points to record that was renamed to repeat in receiver
7.	**Receiver No.**  
Important when using group receiver
### Synchronizing records
After running replication no data is sent to Receiver. To process Record Synchronization Entries there are 2 options. Action **Synchronize** on **Replication Card** processes all pending entries for the replication. Action **Process** on **Record Synchronization Entries** page processes all selected entries.


[Back](master-data-management-system-mdms.md)