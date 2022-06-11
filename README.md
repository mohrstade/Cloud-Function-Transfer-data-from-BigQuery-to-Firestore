# Cloud-Function-Transfer-data-from-BigQuery-to-Firestore

Code for a Cloud Function in NodeJS to transfer data from BigQuery to Firestore. The Cloud Function takes in three parameters in a json object:
{
"bigqueryTableID": "yourBigQueryProject.yourDataset.yourTable",
"firestoreCollection":"theFirestoreCollectionName",
"columnName":"documentID"
}
You need to specify the BigQuery TableID where data is taken from, the Firestore Collection name where data is sent to and the documentID which will be used as unique identifier for the different Firestore documents.
Every row in the BigQuery Table will put in one document in Firestore where the document name is the choosen field of the BigQuery table.
In case documents allready exist with the same documentID the will be overwritten.
