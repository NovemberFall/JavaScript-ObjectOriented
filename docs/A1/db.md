# 2. Database Firebase

### `Storing Data`

- Websites work with data
   
   - blog post, todos, comments, user info, scores etc

- We can store this data in a database
   
   - Firebase(by Google)

![](img/23.png)



### `Firebase && Firestores`

- `Firebase` is known as a backend as a service

- It provides us with a complete backend solution to all of our Websites 

- meaning as front end developers we don't need to worry about setting up a server to do things like interact with a database or run server.

- firebase is an out of the box service which can help us do all of this without having to set up our own server. 

- And the best thing about this is that it's completely free for somall applications and Websites.

### create a new account


![](img/24.png)

- click `Go to console`

- create a new project

![](img/25.png)
![](img/26.png)

- so this area is the control center for the back end of our Website.

- now we can do a lot of set up

- but we focus on `Database`, click `Database`

![](img/27.png)

### Note:

- if we want to learn more about firebase as a whole and the different features, go to YouTube channel.

---
### 

- create a new fire store database

- Now firebase actually comes with two types of database:
    
    1. `Firestore`, which we're going to be using. And that is the new type of database.
    
    2. the older `real time database` as well which is still good. 
  


- now, `click`:

![](img/28.png)
![](img/29.png)

- click `Start collection`

![](img/30.png)

- Now remember documents represent single records and they're very much like `javaScript objects`

- They have `key value pairs`

![](img/31.png)

- see this picture, for `Document ID`, I'm goint to leave because if we leave this blank `firestore` is going to *automatically* generate a unique idea for us. 

- Remember: every `Document` in `firestore` has a unique idea and we can use those ideas later on to go out and query the database and get documents. 

![](img/32.png)

- now we add another `Document`

![](img/33.png)
![](img/34.png)

- now we have our first two `documents` inside that `collection`

### `connecting to firebase`

- The next logical step that it would be to connect to this database and 
  the backend in general from the front end Our web site in the browser

- to do that, we need to copy a little snippet of code from firebase from the back end into the front end of our Web site. 

- And that's goint to allow us to connect to this backend and use services like the firebase firestore database

---

- Now go to `Project Overview`

- click this icon:

![](img/35.png)
![](img/36.png)

- look this piece of codes, this `API key` is a bit like an indentifier, it tells the front end of our website which backend to connect to over. 

- we need to `copy` all of this

`index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Databases</title>
</head>
<body>
  <h1>Databases (Firebase)</h1>
  <!-- The core Firebase JS SDK is always required and must be listed first -->
  <script src="https://www.gstatic.com/firebasejs/6.3.3/firebase-app.js"></script>

  <!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#config-web-app -->

  <script>
    // Your web app's Firebase configuration
    var firebaseConfig = {
      apiKey: "AIzaSyA8vit_XuqDScDXuzYi0ao1OXqSTlJApAQ",
      authDomain: "fir-firstproject-98610.firebaseapp.com",
      databaseURL: "https://fir-firstproject-98610.firebaseio.com",
      projectId: "fir-firstproject-98610",
      storageBucket: "fir-firstproject-98610.appspot.com",
      messagingSenderId: "417666124453",
      appId: "1:417666124453:web:9d6d7fcf65026476"
    };
    // Initialize Firebase
    firebase.initializeApp(firebaseConfig);
  </script>

  <script src="sandbox.js"></script>
</body>
</html>
```

- there's only one more thing to do here and that is to get a reference to our database or to initialize the database. 

### `import a bootstramp library`

`updating the .html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
  <title>Databases</title>
</head>
<body>
  <div class="container my-5">
    <h2>Recipes</h2>
    <ul>
      <li>Mushroom pie</li>
      <li>Veg curry</li>
    </ul>
    <form>
      <label for="recipe">Add a new recipe:</label>
      <div class="input-group">
        <input type="text" class="form-control" id="recipe" required>
        <div class="input-group-append">
          <input type="submit" value="add" class="btn btn-outline-secondary">
        </div>
      </div>
    </form>
  </div>

  <!-- The core Firebase JS SDK is always required and must be listed first -->
  <script src="https://www.gstatic.com/firebasejs/5.8.4/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/5.8.4/firebase-firestore.js"></script>

  <!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#config-web-app -->

  <script>
    // Your web app's Firebase configuration
    var firebaseConfig = {
      apiKey: "AIzaSyA8vit_XuqDScDXuzYi0ao1OXqSTlJApAQ",
      authDomain: "fir-firstproject-98610.firebaseapp.com",
      databaseURL: "https://fir-firstproject-98610.firebaseio.com",
      projectId: "fir-firstproject-98610",
      storageBucket: "fir-firstproject-98610.appspot.com",
      messagingSenderId: "417666124453",
      appId: "1:417666124453:web:9d6d7fcf65026476"
    };
    // Initialize Firebase
    firebase.initializeApp(firebaseConfig);
    const db = firebase.firestore();
  </script>

  <script src="sandbox.js"></script>
</body>

</html>
```

![](img/37.png)
---

### `Getting Collections`

- adding html li elements into our ul innerHtml

```js
const list = document.querySelector('ul');
const addRecipe = (recipe) => {
    let html = `
    <li>
    <div>${recipe.title}
    </li>
    `;
    console.log(html);
    list.innerHTML += html;
}

db.collection('recipes').get().then((snapshot) => {
    //when we have the data
    // console.log(snapshot.docs[0].data());
    snapshot.docs.forEach((doc) => {
        addRecipe(doc.data());
    })
}).catch((error) => {
    console.log(error);
})
```

![](img/2019-08-01-07-10-53.png)

- now I also want to output the time that we created that property 

```js
const list = document.querySelector('ul');
const addRecipe = (recipe) => {
    console.log(recipe.created_at);   //print the created time
    let html = `
    <li>
    <div>${recipe.title}
    </li>
    `;
    console.log(html);
    list.innerHTML += html;
}
```

![](img/2019-08-01-07-32-14.png)


```js
const list = document.querySelector('ul');
const addRecipe = (recipe) => {
    let time = recipe.created_at.toDate();
    let html = `
    <li>
        <div>${recipe.title}</div>
        <div>${time}</div>
    </li>
    `;
    console.log(html);
    list.innerHTML += html;
}

db.collection('recipes').get().then((snapshot) => {
    snapshot.docs.forEach((doc) => {
        console.log(doc.data());
        addRecipe(doc.data());
    })
}).catch((error) => {
    console.log(error);
})
```

![](img/2019-08-01-08-35-24.png)


### `Saving Documents`

- when we actually save a document to our firestore database, 
  what we do is we actuall pass it a javascript object and it saves it as a document

- create an object that looks like that and call it recipe. 

- adding a document

```js
//saving documents
const list = document.querySelector('ul');
const form = document.querySelector('form');

const addRecipe = (recipe) => {
    // console.log(recipe.created_at);
    let time = recipe.created_at.toDate();
    let html = `
    <li>
        <div>${recipe.title}</div>
        <div>${time}</div>
    </li>
    `;
    list.innerHTML += html;
}

db.collection('recipes').get().then((snapshot) => {
    //when we have the data
    // console.log(snapshot.docs[0].data());
    snapshot.docs.forEach((doc) => {
        addRecipe(doc.data());
    })
}).catch((error) => {
    console.log(error);
})

// add documents
form.addEventListener('submit', e => {
    e.preventDefault();
    const now = new Date();
    const recipe = {
        title: form.recipe.value,
        created_at: firebase.firestore.Timestamp.fromDate(now)
    };
    db.collection('recipes').add(recipe).then(() => {
        console.log('recipe added')
    }).catch(error => {
        console.log(error);
    });
})
```

![](img/2019-08-01-10-11-45.png)

- so when we refersh the page, the new document has been added

![](img/2019-08-01-10-16-38.png)











### `Deleting Documents`

- first, what I'd like to do is output some kind of little button in each one of these are like tags 

- and when we click that button, it's going to delete that document from the database

```js
const addRecipe = (recipe) => {
    // console.log(recipe.created_at);
    let time = recipe.created_at.toDate();
    let html = `
    <li>
        <div>${recipe.title}</div>
        <div>${time}</div>
        <button class="btn btn-danger btn-sm my-2">delete</button>
    </li>
    `;
    list.innerHTML += html;
}

```

![](img/2019-08-01-10-47-54.png)

- we bind an `id` to every li element

```js
const addRecipe = (recipe, id) => {
    // console.log(recipe.created_at);
    let time = recipe.created_at.toDate();
    let html = `
    <li data-id="${id}">
        <div>${recipe.title}</div>
        <div>${time}</div>
        <button class="btn btn-danger btn-sm my-2">delete</button>
    </li>
    `;
    list.innerHTML += html;
}

```

![](img/2019-08-01-11-54-47.png)



`get the id`

```js
list.addEventListener('click', e => {
    if (e.target.tagName === 'BUTTON') {
        const id = e.target.parentElement.getAttribute('data-id');
        console.log(id);
    }
})
```

![](img/QQ20190801-115748-HD.gif)

- now we can delete a li element

```js
//deleting data
list.addEventListener('click', e => {
    if (e.target.tagName === 'BUTTON') {
        const id = e.target.parentElement.getAttribute('data-id');
        db.collection('recipes').doc(id).delete().then(() => {
            console.log('recipe delete')
        });
    }
})
```

- but the problem is that you can find no element is deleted because we have to refersh


### `Real-time Listeners`

- since when we delete the li element our UI is not automactically updated

- It would be nice if we could keep our UI or template in sync with our firestore database

- Now a firestore database has `real time` capabilities to do this

- we can set up a `real-time` listener in our javascript code and that listener will actively listen at all times to our database collection

- Then when something changes in the collection like a new document added or a document removed it will get the update back and we can update the UI with it.

```js
//Real-time Listeners
//delete document
const list = document.querySelector('ul');
const form = document.querySelector('form');

const addRecipe = (recipe, id) => {
    // console.log(recipe.created_at);
    let time = recipe.created_at.toDate();
    let html = `
    <li data-id="${id}">
        <div>${recipe.title}</div>
        <div>${time}</div>
        <button class="btn btn-danger btn-sm my-2">delete</button>
    </li>
    `;
    list.innerHTML += html;
}

const deleteRecipe = (id) => {
    const recipes = document.querySelectorAll('li');
    recipes.forEach(recipe => {
        if (recipe.getAttribute('data-id') === id) {
            recipe.remove();
        }
    })
}

db.collection('recipes').get().then((snapshot) => {
    snapshot.docs.forEach((doc) => {
        addRecipe(doc.data(), doc.id);
    })
}).catch((error) => {
    console.log(error);
})

//get documents
db.collection('recipes').onSnapshot(snapshot => {
    // console.log(snapshot.docChanges());
    snapshot.docChanges().forEach(change => {
        const doc = change.doc;
        if (change.type === 'added') {
            addRecipe(doc.data(), doc.id);
        } else if (change.type === 'removed') {
            deleteRecipe(doc.id);
        }
    })
});//every time the collection changes in any way, firestore takes a snapshot of that collection 
//an the snapshot represents the state of that conllection at that moment in time



// add documents
form.addEventListener('submit', e => {
    e.preventDefault();
    const now = new Date();
    const recipe = {
        title: form.recipe.value,
        created_at: firebase.firestore.Timestamp.fromDate(now)
    };
    db.collection('recipes').add(recipe).then(() => {
        console.log('recipe added')
    }).catch(error => {
        console.log(error);
    });
})

//deleting data
list.addEventListener('click', e => {
    if (e.target.tagName === 'BUTTON') {
        const id = e.target.parentElement.getAttribute('data-id');
        db.collection('recipes').doc(id).delete().then(() => {
            console.log('recipe delete')
        });
    }
})

```



### `Unsubscribing`

```js
/Real-time Listeners
//Unsubscribing
const list = document.querySelector('ul');
const form = document.querySelector('form');
const button = document.querySelector('button');

const addRecipe = (recipe, id) => {
    // console.log(recipe.created_at);
    let time = recipe.created_at.toDate();
    let html = `
    <li data-id="${id}">
        <div>${recipe.title}</div>
        <div>${time}</div>
        <button class="btn btn-danger btn-sm my-2">delete</button>
    </li>
    `;
    list.innerHTML += html;
}

const deleteRecipe = (id) => {
    const recipes = document.querySelectorAll('li');
    recipes.forEach(recipe => {
        if (recipe.getAttribute('data-id') === id) {
            recipe.remove();
        }
    })
}

db.collection('recipes').get().then((snapshot) => {
    snapshot.docs.forEach((doc) => {
        addRecipe(doc.data(), doc.id);
    })
}).catch((error) => {
    console.log(error);
})

//get documents
const unsub = db.collection('recipes').onSnapshot(snapshot => {
    // console.log(snapshot.docChanges());
    snapshot.docChanges().forEach(change => {
        const doc = change.doc;
        if (change.type === 'added') {
            addRecipe(doc.data(), doc.id);
        } else if (change.type === 'removed') {
            deleteRecipe(doc.id);
        }
    })
});//every time the collection changes in any way, firestore takes a snapshot of that collection 
//an the snapshot represents the state of that conllection at that moment in time




// add documents
form.addEventListener('submit', e => {
    e.preventDefault();
    const now = new Date();
    const recipe = {
        title: form.recipe.value,
        created_at: firebase.firestore.Timestamp.fromDate(now)
    };
    db.collection('recipes').add(recipe).then(() => {
        console.log('recipe added')
    }).catch(error => {
        console.log(error);
    });
})

//deleting data
list.addEventListener('click', e => {
    if (e.target.tagName === 'BUTTON') {
        const id = e.target.parentElement.getAttribute('data-id');
        db.collection('recipes').doc(id).delete().then(() => {
            console.log('recipe delete')
        });
    }
})


//unsub from database changes
button.addEventListener('click', () => {
    unsub();
    console.log('unsubscribed from collection changes')
})
```



