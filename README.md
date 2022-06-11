# Cloud-Function-Transfer-data-from-BigQuery-to-Firestore

<h2>Intro</h2>
Code for a Cloud Function in NodeJS to transfer data from BigQuery to Firestore.In case documents allready exist with the same documentID the will be overwritten /updated. The Cloud Function needs a JSON object with three parameters to work accordingly:

```javascript
{
"bigqueryTableID": "yourBigQueryProject.yourDataset.yourTable",
"firestoreCollection":"theFirestoreCollectionName",
"columnName":"documentID"
}
```
You need to specify the BigQuery TableID where data is taken from, the Firestore Collection name where data is sent to and the documentID which will be used as unique identifier for the different Firestore documents.
Every row in the BigQuery table will be put in one document in Firestore where the document name is one choosen field of the BigQuery table named columnName in the JSON Object.

<h2>How to setup it up</h2>
<ol>
  <li><b>Create a service account</b><br>Create a Service Account in Google Cloud Platform to use in the Cloud Function created later. Roles needed: BigQuery Job User, Cloud Datastore User, Cloud Functions Invoker</li>
  <li><b>Create the Cloud Function</b><br>Create a Cloud Function with Trigger Type HTTP and with "Allow unauthenticated invocations" enabled. Choose the service account created in step 1. As runtime choose Node.js 16 and make sure the entry point is "init". Copy the code from this repository including the package.json.</li>
  <li><b>Create a scheduled job</b><br>To run the data transfer frequently you can use the Cloud Scheduler. Create a job with content-type: "application/json" and put the JSON object into the body.
</ol>
