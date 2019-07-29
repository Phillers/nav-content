# How to: Create and Process Replication
## Master Company Setup
### No. Series
It is necessary to set up 2 numbering series:
1.	Data Set Nos.
2.	Replication Nos.
This can be done using standard NAV No. Series page.
### MDMS Setup
Following fields should be set up in Master Company:
1.	Data Set Nos.
Indicates No. Series used for numbering new Data Set records.

2.	Replication Nos.
Indicates No. Series used for numbering new Replication records.

3.	Master Company
Indicates that current company is Master Company. This enables a number of functionalities, including blocking of certain actions against records from tables that are part of active data set.

4.	Block Record Rename
When selected, users will not be able to rename any record from synchronized tables.

5.	Records per Sync. Message
Number of records send per one message, the smaller the datasets the larger the number can be, 0 will result in default value 300, in case of errors needs to be lowered

6.	Import Error Action
Specifies system behavior after importing of new file fails. Available values are:
•	Continue & Move to Archive: Legacy option. Even though import fails, file will be moved to ARCHIVE folder.
•	Continue & Keep File: File will not be moved to ARCHIVE and will stay in INBOX. Therefore, system will try to import it again 
•	Stop & Show Error: Error will be thrown, which will stop processing.

## User Permission & User Setup
As part of MDMS module, new permission set has been created: MDMS. It contains all necessary permissions to set up & execute module functions.
On MDMS User Setup page (available under: MDMS / MDMS User Setup) there are following fields:
1.	User ID
Contains user ID. 

2.	Receiver No.
Assigns user to Receiver. This connection is necessary when processing record-level replication. For more information about record-level replication, see User Guide.

3.	MDMS Super User
Indicates that user is Master Data Super User. When selected, user will be able to perform all activities against records that are part of synchronized data sets. It is possible to block delete / rename actions in Master Company in MDMS Setup. In Receiver Company it depends on settings on replicated Data Set. When system recognizes current user as Master Data Super User, no restrictions will apply. For more details refer to User Guide. 

#	Receivers
Receiver is a company that will receive data sent from Master Company.
**In each receiver company, two Web Services need to be published, codeunits 20020709 and 20020716.**
*Copy SOAP URL of one of them.*

To set up a receiver, Receiver Card needs to be opened from MDMS / Receivers.
Following fields need to be set up:
1.	No.
Receiver No.

2.	Description
Receiver Description

3.	Language Code
Language Code

4.	WebServices Address
Paste copied url here, but ending after the company name and before the word codeunit. For example:
http://SERVER:7047/INSTANCE/WS/Receiver/Codeunit/ReceiverWS should be:
http://SERVER:7047/INSTANCE/WS/Receiver

5.	ReceiverWS Codeunit Name and Record Synchronization Codeunit name
Service Names given to those two codeunits on Web Services Page 

6.	WebServices Username and Password
Credentials needed to log on the remote webservices

[Back](master-data-management-system-mdms.md)