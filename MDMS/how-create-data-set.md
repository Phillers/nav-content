# How to: Create a Data Set
Data Set contains information about structure of data being replicated.
Data Sets can be found under  **MDMS / Data Sets**.

Following fields are available in Data Set header:
1.	**No.**  
Data Set unique identifier
2.	**Description**  
Data Set description
3.	**Last Date Modified**  
Read-only field. Contains date of last modification
4.	**Status**  
Read-only field, contains Data Set status. Status may be either Open or Released and can be adjusted using Release and Reopen actions.

Following fields are available in Data Set lines:
1.	**Code**  
Data Set line unique identifier
2.	**Name**  
Data Set line description
3.	**Table No.**  
No. of table being replicated
4.	**Table Name**  
Name of table being replicated, filled in automatically upon entering Table No.
5.	**On Record Exists**  
Defines action which will be taken when replicated record is found to be already existing in target database. Possible actions are Update and Skip.
6.	**Record-Level Replication**  
Specifies whether all table data should be replicated or user (assigned MDMS Receiver role) should manually mark records which they want to be replicated to their local database 
7.	**Disable Local Insert** 
While this field is selected, users will not be able to insert new records in their local database
8.	**Disable Local Delete**  
While this field is selected, users will not be able to delete records in their local database
9.	**Block Exclude Filter**  
Specify a filter (using C/AL SETVIEW syntax) to exclude certain records from blocking rules.
Example filters:
•	Cross-Reference Type=FILTER(<>Bar Code)
•	Code=FILTER('FA CIP')
•	"Dimension Code"=FILTER('FA CIP')
•	"No."=FILTER(11111..11198|11211..11297)
10.	**Run Trigger on Insert**  
When new record is inserted to local database, INSERT(TRUE) will be used during the operation. By default, it is INSERT(FALSE).
11.	**Run Trigger on Modify** 
When record is updated in local database, MODIFY(TRUE) will be used during the operation. By default, it is MODIFY(FALSE).
12.	**Target Table No.**  
Here you can specify Table No. records should be inserted to in Receiver company. Default value is 0 = records will be transferred to the same table they are exported from.

User can set up which fields should be included in the Data Set using **Line / Show Details** function.
Following fields are available on Data Set Line Details page:
1.	**Code**  
Unique identifier of Data Set field
2.	**Field No.**  
Field number
3.	**Field Name**  
Field name
4.	**Target Field No.**  
Number of target field. It is therefore possible to set up Data Set to import the data to another field from the same table
5.	**Validate Field**  
Indicates whether field should be validated upon importing on the receiver side
6.	**Disable Local Modify**  
Indicates whether editing field should not be allowed locally, on the receiver side
7.	**Field Type**  
Type of the field
8.	**Processing Order**  
Order in which record fields will be processed. This is particularly important when considering data validation flow
9.	**Table No.**  
Table Number
10.	**Keep Local Value**  
Push field value from global company to local company, but do not overwrite afterwards. It will be possible to adjust field’s value locally and this value will be kept.	
11.	**Skip Export**  
Select this field if you would like to skip current field from the export.

Note: It is also possible to add many fields at once, using **Add Fields** function:

### Releasing / Reopening
After all necessary setup has been performed, it is necessary to mark Data Set card as completed using **Functions / Release** action which will change its status to Released. Data Set has to be released prior to be included on any Replications. If user wants to make any further adjustments to previously released Data Set, it is necessary to reopen it first using **Functions / Reopen** action.
###	Data Set filters
Using **Line / Show Filters** action it is possible to specify additional filters that will be applied to data set records while processing replication.
NOTE: If filters are defined both on Data Set and on Replication, for the same table, filters on Data Set level will be overwritten.
### Data Set Line Relation
Using **Line / Show Relation** action it is possible to specify relation between indented record and its parent.

[Back](master-data-management-system-mdms.md)