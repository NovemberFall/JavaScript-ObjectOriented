# 1. firebase-ta

### `FIREBASE AND FIRESTORE NOTES `


### `QUERY REFERENCE AND QUERY SNAPSHOT `

- Firestore library gives us one of two different types of potential objects 
    
    1. Query Reference 
    
    2. Query Snapshot 

- A query is a request we make to firestore to give us something from the database 

- Firestore returns us two types of objects: references and snapshots Of these objects, 
  they can either be documents or collection versions. 

- Firestore will always return us these objects, even if nothing exists at from that query 

### `QUERY REFERENCE `

- A QueryReference is simply an object that represent the current place in the database 
  that we are querying. We get them by calling either

-  

`firestore.doc('/users/:userId')`

`firestore.collection('/users')`

- The query reference object does not have the actual data of the collection or document.
  It instead has properties that tell us details about it, 
  or the method to get the snapshot object which gives us the data we are looking for. 

### `Document Reference VS Collection Reference `

- We use documentRef objects to perform our CRUD methods (create, read , update, delete ).
  The documentRef methods are

```
.set() 
.get() 
.update() 
.delete() 
```

- We can also add documents to collections using the collectionRef object using the .add() method 

`collectionRef.add({//value:prop})`

- We get the snapshotObject from the referenceObject using .get() method i.e documentRef.get() 
  or collectionRef.get() 

- documentRef returns a documentSnapshot object. 

- collectionRef returns a querySnapshot object 

- exists property on the snapshot object tells us whether there is any data there or not. 

### `DOCUMENT SNAPSHOT `

- We get a documentSnapshot object from our documentReference object 
  The documentReference object allows us to check if a document exists at this query using the .exists property which returns a boolean. 
  We can also get the actual properties on the object by calling .data() method which return us a JSON object of the document. 

### `FIREBASE AUTH `

- Firebase Authentication for Firebase backed applications 

- Client(Browser) and Server 

- From the frontend we connect to the firebase backend via the Firebase SDK and 
  that allows us to communicate with all the Firebase Services that we need from the frontend of the application 

### `Firebase Authentication` 

- How Authentication Works ! (Theory Point of View)

- For eg we have some kind of form in our application that may be the Login Form or the Registration 
  Form and we capture user credentials using that form then they are sent securely to the server 
  via the login method or the registration method provided by Firebase SDK.Then on the server, 
  Firebase validates those credentials and send back an authentication token to the browser 
  and then we can access data in our browser from this token for example name or email of the user 
  that got just loggedin or registered. Now when the requests are made to the firebase server 
  after login for example to the firestore or the cloud functions or something like that 
  then this token is sent along for the ride and these are the services they have access to that information on them too.

- When some request is made to change some kind of data in the firestore, 
  Firestore will be able to look at the auth token of that request and 
  then protect data based on that user token.We can protect sensitive database data from any user 
  who is not an admin and we can tell that from the token that comes along for the ride 

- Once the user is logged in to our application then the firebase persists the users state 
  so that means refreshing the page does not mean that they are logged out they will be still be loggedin 

- All the Server Side Configuration that you want to enable is done using Firebase Console. 
  This will provide us all the features like Cloud Functions or the Firestore database that is used 

```js
STEP 1 : Set up the SignIn method (by default it is not set )

STEP 2 : 
Provider                            Status
Email/Password                      Enable 

Enable the provider Email/Password to the Enable Status 
This is for making the users loggedin to our application 
This is the email and password authentication that we can 
configure using this Step 2 

We want to add a new user not from the Firebase console 
but from the frontend of our application 

FIRESTORE 
Firebase Database which is the Cloud Firestore database 

We have two kind of databases here 
1. Real time Firebase which is the older one 
2. The newer version is the Firestore which is awesome as 
well 

STEP 3 : Go to the database option in the Develop Section 

STEP 4 : Click on the Create Database button 

STEP 5 : Check the Start in Test Mode radio button and 
click enable (This is for initial development phase)
This will let us to easily interact with the database 
without having to worry about the security rules 
In the locked mode authentication is required for reading 
and writing the data.Once the application is done,we will 
change the mode to the locked mode. 

STEP 6: We can create collection either using the Firestore 
or through our application. 

UI AND FIRESTORE SECURITY RULES 
Firestore security rules where only the authenticated users may be 
allowed access to certain resources like create guides and all. 

Custom Claims in Firebase and Firestore applications 

Firebase Authentication 
UserId 
Email 
CUSTOM CLAIMS : 
    admin : true
    premium : true 

By using the concept of custom claims, we can ensure that only the users 
that have special privileges will be able to create guides and the normal users 
can only view them if you have the admin privileges then only allow the creation of 
the guides.

Client(Browser) 

user has admin claim ? 

If yes, show the admin UI 
If no, show the normal UI 

Server Side  

If user has admin claim ? 
If yes, allow access for data. 
If no, block the data access 

Cloud Functions  
Cloud functions run on the server 
Good for code you do not want to expose on the client 
Perform tasks not available to client users 
Callable from the frontend of the application 

Firebase cloud functions are really very cool 
they allow to run some code on the serverside only 
Even though the cloud functions run on the server we can call them from 
the frontend of the application and if we have the required credentials 
and want to make a user an admin, then we can attach our custom claim 
to our cloud function 
```