# Approval Interface

## Description
A caiApprovalInterface Component used to implement an approval interface.


## How to use
```
Approval_Interface_Configuration__c aic=new Approval_Interface_Configuration__c();
   aic.Child_Level_1__c='Return_Sales_Order_Line_Item__c';
   aic.Approved_Header_Column_Name__c=[{
      "type": "url",
      "fieldName": "link",
      "label": "Sales Order Number",
      "initialWidth": 300,
      "typeAttributes": { "label": { "fieldName": "Name" },
      "target": "_blank"}
      },
      {
      "type": "text",
      "fieldName": "Order_Status__c",
      "label": "Order Status",
      "initialWidth": 200
      } ];
   aic.UGDN_Number__c='20004743';
   aic.Approve_Reject_By_Status__c='Pending';
   aic.Stage__c='pending';
   aic.Approved_SOQL_Statement__c='select id,Name,Order_Status__c,Sub_Status__c,       Refusal__c,     Return_Type__c,Necessary_Technical_Inspection__c,RSO_Raised_By__c,      (select id,Name from Return_Sales_Order_Line_Items__r) from Return_Sales_Order__c where Order_Status__c = 'Approved'';
   aic.sObject_API_Name__c='Return_Sales_Order__c';
   aic.Profile_API_Name__c='Brazil Customer Service User';
   aic.Cancelled_Header_Column_Name__c=[
            {
         "type": "url",
         "fieldName": "link",
         "label": "Sales Order Number",
         "initialWidth": 300,
         "typeAttributes": { "label": { "fieldName": "Name" },
         "target": "_blank"}
         },{
               "type": "text",
               "fieldName": "Order_Status__c",
               "label": "Order Status",
               "initialWidth": 200
            },
         ];
   aic.Cancelled_SOQL_Statement__c='select id,Name,Order_Status__c,Sub_Status__c,Refusal__c,Return_Type__c,Necessary_Technical_Inspection__c,RSO_Raised_By__c,(select id,Name from Return_Sales_Order_Line_Items__r) from Return_Sales_Order__c where Order_Status__c = 'Cancelled'';
   aic.Rejected_SOQL_Statement__c='select id,Name,Order_Status__c,Sub_Status__c,Refusal__c,Return_Type__c,Necessary_Technical_Inspection__c,RSO_Raised_By__c,(select id,Name from Return_Sales_Order_Line_Items__r) from Return_Sales_Order__c where Order_Status__c = 'Rejected'';
        aic.Rejected_Header_Column_Name__c=[
            {
         "type": "url",
         "fieldName": "link",
         "label": "Sales Order Number",
         "initialWidth": 300,
         "typeAttributes": { "label": { "fieldName": "Name" },
         "target": "_blank"}
         },{
               "type": "text",
               "fieldName": "Order_Status__c",
               "label": "Order Status",
               "initialWidth": 200
            },
         ];
   aic.Pending_At_Higher_Authority_Header_Col__c='[
            {
         "type": "url",
         "fieldName": "link",
         "label": "Sales Order Number",
         "initialWidth": 300,
         "typeAttributes": { "label": { "fieldName": "Name" },
         "target": "_blank"}
         },{
               "type": "text",
               "fieldName": "Order_Status__c",
               "label": "Order Status",
               "initialWidth": 200
            },
               
         ]';
    aic.Pending_At_Higher_Authority_SOQL_State__c='select id,Name,Order_Status__c,Sub_Status__c,Refusal__c,Return_Type__c,RSO_Raised_By__c,Sales_Office_Manager__c,(select  id,Name from Return_Sales_Order_Line_Items__r) from Return_Sales_Order__c where
         (Return_Type__c = 'Commercial' OR Return_Type__c = 'Credit' OR Return_Type__c = 'Formulation' OR Return_Type__c = 'Packaging' OR Return_Type__c = 'Customer' OR Return_Type__c = 'Missing' OR Return_Type__c = 'Logistics')
         AND
      ((RSO_Raised_By__c = 'Sales Rep' OR RSO_Raised_By__c = 'Customer Service' OR RSO_Raised_By__c = 'Key Account Manager' OR RSO_Raised_By__c = 'Logistics' OR RSO_Raised_By__c = 'Sales District Manager') AND (Order_Status__c = 'Pending') AND ( Sub_Status__c = 'Pending At CFO' OR Sub_Status__c = 'Pending At Supply Director' OR Sub_Status__c = 'Pending At Inspection Team' ))';

        insert aic;
```

## Properties And Events
```
sObject_API_Name__c: This field stores the API name of the Salesforce object for which the  approval interface configuration is defined. It specifies the object that is associated with the approval process.
Child_Level_1__c: This field is used to define the child level 1 object for the approval process. It represents the related object that is associated with the main object involved in the approval process.
UGDN_Number__c: This field stores the UGDN for the approval interface configuration. It is used to specify a specific user group or distribution number for the approval process.
Stage__c: This field stores the stages of the approval process for the specific object. It defines the different stages through which an approval request can progress.
Approved_SOQL_Statement__c: This field contains the SOQL (Salesforce Object Query Language) statement for retrieving approved records in the approval process. It specifies the query used to fetch records that have been approved.
Open_SOQL_Statement__c: This field contains the SOQL statement for retrieving open records in the approval process. It specifies the query used to fetch records that are currently open and awaiting approval.
Failed_In_Process_SOQL_Statement__c: This field contains the SOQL statement for retrieving failed records in the approval process. It specifies the query used to fetch records that have failed during the approval process.
Pending_At_Higher_Authority_SOQL_State__c: This field contains the SOQL statement for retrieving pending records awaiting higher authority approval in the approval process. 
Rejected_SOQL_Statement__c: This field contains the SOQL statement for retrieving rejected records in the approval process. 
Pending_SOQL_Statement__c: This field contains the SOQL statement for retrieving pending records in the approval process. 
Cancelled_SOQL_Statement__c: This field contains the SOQL statement for retrieving canceled records in the approval process. 
Profile_API_Name__c: This field stores the API name of the Salesforce profile associated with the approval interface configuration. 
```