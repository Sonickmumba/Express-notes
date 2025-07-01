# Introduction to Server-Side Frameworks with Express.js

Let's go over server-side frameworks, specifically how Express.js works as a server-side framework.

## What is a Server-Side Framework

Let's first start with what a framework is — which is a collection of code to make it easier to accomplish a specific task. A framework is particular in that developers must follow the rules and syntax put forth by the framework to use it properly. With that in mind, a server-side framework is used to run web applications and handle web development workflows on the server-side or back-end. This workflow might include things like accessing databases, generating HTML, handling URL routing, and more!

## Why Use a Server-Side Framework?

As you just read, there's a lot to consider when constructing a back-end. A server-side framework can handle a lot of the back-end responsibilities without you needing to come up with a custom solution, which saves a lot of time. Other benefits could include:

- Access to libraries built to work with the framework
- Existing resources and documentation for solving common problems
- Improved security

There are some tradeoffs to consider as well — as noted earlier, you would need to learn the patterns of the framework. Now let's look at a specific example of a server-side framework, Express.js.

## Node.js and Express.js

As you recall, Node.js is an open-source runtime environment for executing JavaScript outside of a browser. You can create a back-end entirely with Node.js. However, you can also use Express.js, a server-side framework written in JavaScript and built to work with Node.js. The Express.js framework comes with included code that makes implementing some core functionality much quicker than doing it from scratch. By using Express, you have a simpler developer experience and thus can focus more on business logic (functionality).

Let's take a look at a code snippet that showcases Express code. The code below sets up a route on a server:

```javascript
const express = require('express');
const app = express();
  
app.get('/', (req, res) => {
  res.send('<h1>Hello from your Express.js server!!</h1>');
});
  
app.listen(8000, () => {
  console.log('Server listening on port 8000');
});

Which would render load on localhost:8000:
```
![image](https://github.com/user-attachments/assets/20304516-baf2-4f64-b2ba-4a65e919bb87)


With a few lines of code, you can see the simplistic approach Express uses for back-end development. It is also because of Express.js’s minimalist approach and built-in features, Express is one of the most popular frameworks to use with Node. You will see this first-hand as you get to learn the Express framework.
## Review
Good work, you now know more about server-side frameworks! These frameworks come with specific syntax and rules but help developers quickly set up a back-end. Express.js is an example of a server-side framework that is built upon Node. You’ll learn more about what else Express has to offer in the upcoming lesson and see first-hand why it’s so popular.

Here's the content formatted in GitHub-flavored Markdown:


# Learn Express Routes

## Introduction  
**1 min**  

A huge portion of the Internet’s data travels over HTTP/HTTPS through request-response cycles between clients and servers. Every time that you use a website, your browser sends requests to one or many servers requesting resources. Every image, meme, post, and video is requested by a client and sent in a response from a server.

Express is a powerful but flexible Javascript framework for creating web servers and APIs. It can be used for everything from simple static file servers to JSON APIs to full production servers.

In this lesson, you will be fixing a machine called Express Yourself in the browser. The machine is supposed to provide functionality for clients to interact with various Expressions: JavaScript objects each containing ids, names, and emojis. Currently, it looks nice, but nothing works since there is no server in place! You will be learning all the necessary skills to implement an API allowing clients to Create, Read, Update, and Delete Expressions. These four functionalities together are known as CRUD, and they form the backbone of many real-life APIs.

## Starting A Server  
**8 min**  

Express is a Node module, so in order to use it, we will need to import it into our program file. To create a server, the imported express function must be invoked.

```javascript
const express = require('express');
const app = express();
```

On the first line, we import the Express library with `require`. When invoked on the second line, it returns an instance of an Express application. This application can then be used to start a server and specify server behavior.

The purpose of a server is to listen for requests, perform whatever action is required to satisfy the request, and then return a response. In order for our server to start responding, we have to tell the server where to listen for new requests by providing a port number argument to a method called `app.listen()`. The server will then listen on the specified port and respond to any requests that come into it.

The second argument is a callback function that will be called once the server is running and ready to receive responses.

```javascript
const PORT = 4001;
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

In this example, our `app.listen()` call will start a server listening on port 4001, and once the server is started it will log `'Server is listening on port 4001'`.

```javascript
// Import the express library here
const express = require('express');
// Instantiate the app here
const app = express();

const PORT = process.env.PORT || 4001;

// Invoke the app's `.listen()` method below:
app.listen(PORT, () => {
  console.log('The server is listening for requests')
})
```

## Writing Your First Route  
**9 min**  

Once the Express server is listening, it can respond to any and all requests. But how does it know what to do with these requests? To tell our server how to deal with any given request, we register a series of routes. Routes define the control flow for requests based on the request’s path and HTTP verb.

For example, if your server receives a GET request at `/monsters`, we will use a route to define the appropriate functionality for that HTTP verb (GET) and path (`/monsters`).

The path is the part of a request URL after the hostname and port number, so in a request to `localhost:4001/monsters`, the path is `/monsters` (in this example, the hostname is `localhost`, the port number is `4001`).

The HTTP verb is always included in the request, and it is one of a finite number of options used to specify expected functionality. GET requests are used for retrieving resources from a server, and we will discuss additional request types in later exercises.

Express uses `app.get()` to register routes to match GET requests. Express routes (including `app.get()`) usually take two arguments, a path (usually a string), and a callback function to handle the request and send a response.

```javascript
const moods = [{ mood: 'excited about express!'}, { mood: 'route-tastic!' }];
app.get('/moods', (req, res, next) => {
  // Here we would send back the moods array in response
});
```

The route above will match any GET request to `/moods` and call the callback function, passing in two objects as the first two arguments. These objects represent the request sent to the server and the response that the Express server should eventually send to the client.

If no routes are matched on a client request, the Express server will handle sending a 404 Not Found response to the client.

```javascript
const express = require('express');
const app = express();

const PORT = process.env.PORT || 4001;
// Use static server to serve the Express Yourself Website
app.use(express.static('public'));

// Open a call to `app.get()` below:
app.get('/expressions', (req, res, next) => {
  console.log(req);
})

app.listen(PORT, () => {
  console.log(`Listening on port ${PORT}`);
});
```

# Sending A Response  
**6 min**   

HTTP follows a one request-one response cycle. Each client expects exactly one response per request, and each  
server should only send a single response back to the client per request. The client is like a customer at a restaurant ordering a large bowl of soup: the request is sent through the wait staff, the kitchen prepares the soup, and after it is prepared, the wait staff returns it to the customer. In the restaurant, it would be unfortunate if the soup never arrived back to the customer, but it would be equally problematic if the customer was given four large bowls of soup and was asked to consume them all at the exact same time. That's impossible with only two hands!  

Express servers send responses using the `.send()`  method on the response object. `.send()` will take any input and include it in the response body.  

```javascript
const monsters = [
  { type: 'werewolf' }, 
  { type: 'hydra' }, 
  { type: 'chupacabra' }
];
app.get('/monsters', (req, res, next) => {
  res.send(monsters);
});
```

In this example, a GET /monsters request will match the route, Express will call the callback function, and the res.send() method will send back an
array of spooky monsters.

In addition to .send(), .json() can be used to explicitly send JSON-formatted responses. .json() sends any JavaScript object passed into it.
```javascript
const express = require('express');
const app = express();
const { seedElements } = require('./utils');

// Serves Express Yourself website
app.use(express.static('public'));

const PORT = process.env.PORT || 4001;

const expressions = [];
seedElements(expressions, 'expressions');

// Get all expressions
app.get('/expressions', (req, res, next) => {
  // console.log(req);
  res.send(expressions)
});

app.listen(PORT, () => {
  console.log(`Listening on port ${PORT}`);
});
```
# Matching Route Paths  
**3 min**  

Express tries to match requests by route, meaning that if we send a request to `<server address>:<port number>/api-endpoint`, the Express 
server will search through any registered routes in order and try to match `/api-endpoint`.  

Express searches through routes in the order that they are registered in your code. The first one that is matched will be used, and its callback will be called.  

In the example to the right, you can see two `.get()` routes registered at `/another-route` and `/expressions`. When a `GET /expressions` request arrives to the Express server, it first checks `/another-route`'s path because it is registered before the `/expressions` route. Because `/another-route` does not match the path, Express moves on to the next registered
middleware. Since the route matches the path, the callback is invoked, and it sends a response.  

If there are no matching routes registered, or the Express server has not sent a response at the end of all matched routes, it will automatically send back a `404 Not Found` response, meaning that no routes were matched or no response was ultimately sent by the registered routes.

![image](https://github.com/user-attachments/assets/41c84e8c-97cf-4f3a-ba3a-57f2caa96a4a)

# Getting A Single Expression
** 12min **

Routes become much more powerful when they can be used dynamically. Express servers provide this functionality with named route parameters. Parameters are route path segments that begin with `:` in their Express route definitions. They act as wildcards, matching any text at that path segment. For example `/monsters/:id` will match both `/monsters/1` and `/monsters/45`.

Express parses any parameters, extracts their actual values, and attaches them as an object to the request object: `req.params`. This object's keys are any parameter names in the route, and each key's value is the actual value of that field per request.

```javascript
const monsters = { 
  hydra: { height: 3, age: 4 }, 
  dragon: { height: 200, age: 350 } 
};

// GET /monsters/hydra
app.get('/monsters/:name', (req, res, next) => {
  console.log(req.params); // { name: 'hydra' }
  res.send(monsters[req.params.name]);
});
```
In this code snippet, a .get() route is defined to match /monsters/:name path. When a GET request arrives for /monsters/hydra, the callback is called. Inside the callback, req.params is an object with the key name and the value hydra, which was present in the actual request path.

The appropriate monster is retrieved by name (the object key) from the monsters object and sent back to the client with res.send().
```javascript
const express = require('express');
const app = express();

// Serves Express Yourself website
app.use(express.static('public'));

const { getElementById, seedElements } = require('./utils');

const expressions = [];
seedElements(expressions, 'expressions');

const PORT = process.env.PORT || 4001;

app.get('/expressions', (req, res, next) => {
  res.send(expressions);
});

// Route with parameter
app.get('/expressions/:id', (req, res, next) => {
  res.send(getElementById(req.params.id, expressions))
});

app.listen(PORT, () => {
  console.log(`Listening on port ${PORT}`);
});
```

# Setting Status Codes  
**8 min**  

Express allows us to set the status code on responses before they are sent. Response codes provide information to clients about how their requests were handled. Until now, we have been allowing the Express server to set status codes for us. For example, any `res.send()` has by default sent a `200 OK` status code.  

The `res` object has a `.status()` method to allow us to set the status code, and other methods like `.send()` can be chained from it.  

```javascript
const monsterStoreInventory = { fenrirs: 4, banshees: 1, jerseyDevils: 4, krakens: 3 };
app.get('/monsters-inventory/:name', (req, res, next) => {
  const monsterInventory = monsterStoreInventory[req.params.name];
  if (monsterInventory) {
    res.send(monsterInventory);
  } else {
    res.status(404).send('Monster not found');
  }
});
```
In this example, we've implemented a route to retrieve inventory levels from a Monster Store. Inventory levels are kept in the monsterStoreInventory variable. When a request arrives for /monsters-inventory/mothMen, the route matches and so the callback is invoked. req.params.name will be equal to 'mothMen' and so our program accesses monsterStoreInventory['mothMen']. Since there are no mothMen in our inventory, res.status() sets a 404 status code on the response, and .send() sends the response.

# Matching Longer Paths  
**2 min**  

Parameters are extremely helpful in making server routes dynamic and able to respond to different inputs. Route parameters will match anything in their specific part of the path, so a route matching `/monsters/:name` would match all the following request paths:
/monsters/hydra
/monsters/jörmungandr
/monsters/manticore
/monsters/123


In order for a request to match a route path, it must match the entire path, as shown in the diagram to the right. The request arrives for `/expressions/1`. It first tries to match the `/expressions` route, but because it has additional path segments after `/expressions`, it does not match this route and moves on to the next. It matches `/expressions/:id` because `:id` will match any value at that level of the path segment. The route matches, so the Express server calls the callback function, which in turn handles the request and sends a response.

![image](https://github.com/user-attachments/assets/f61dc6b7-71cf-4589-9f8a-fdcb3097f7cb)


# Other HTTP Methods  
**3 min**  

The HTTP Protocol defines a number of different method verbs with many use cases. So far, we have been using the `GET` request which is probably the most common of all. Every time your browser loads an image, it is making a `GET` request for that file!

This course will cover three other important HTTP methods: `PUT`, `POST`, and `DELETE`. Express provides methods for each one: `app.put()`, `app.post()`, and `app.delete()`.

`PUT` requests are used for updating existing resources. In our Express Yourself machine, a `PUT` request will be used to update the name or emoji of an expression already saved in our database. For this reason, we will need to include a unique identifier as a route parameter to determine which specific resource to update.

# Using Queries  
**16 min**  

You may have noticed in the previous exercise that our PUT route had no information about how to update the specified expression, just the id of which expression to update. It turns out that there was more information in the request in the form of a query string. Query strings appear at the end of the path in URLs, and they are indicated with a `?` character. For instance, in `/monsters/1?name=chimera&age=1`, the query string is `name=chimera&age=1` and the path is `/monsters/1/`.

Query strings do not count as part of the route path. Instead, the Express server parses them into a JavaScript object and attaches it to the request body as the value of `req.query`. The `key:value` relationship is indicated by the `=` character in a query string, and key-value pairs are separated by `&`. In the above example route, the `req.query` object would be `{ name: 'chimera', age: '1' }`.

```javascript
const monsters = { '1': { name: 'cerberus', age: '4' } };
// PUT /monsters/1?name=chimera&age=1
app.put('/monsters/:id', (req, res, next) => {
  const monsterUpdates = req.query;
  monsters[req.params.id] = monsterUpdates;
  res.send(monsters[req.params.id]);
});
```
Here, we have a route for updating monsters by ID. When a PUT /monsters/1?name=chimera&age=1 request arrives, our callback function is called and we create a monsterUpdates variable to store req.query. Since req.params.id is '1', we replace monsters['1']'s value with monsterUpdates. Finally, Express sends back the new monsters['1'].

When updating, many servers will send back the updated resource after the updates are applied so that the client has the exact same version of the resource as the server and

Preview: A database is a collection of structured information stored so it can be easily accessed and updated. In a computer system, databases are commonly accessed through a database management system, or DBMS.

database.


# Matching By HTTP Verb  
**1 min**  

Express matches routes using both path and HTTP method verb. In the diagram to the right, we see a request with a `PUT` verb and `/expressions` (remember that the query is not part of the route path).  

The path for the first route matches, but the method verb is wrong, so the Express server will continue to the next registered route. This route matches both method and path, and so its callback is called, the necessary updating logic is executed, and the response is sent.

![image](https://github.com/user-attachments/assets/3bb11fe4-516e-4bf6-8175-78e67e9eb18e)


# Creating An Expression  
**12 min**  

`POST` is the HTTP  

**Preview:** [A method is a small piece of code](#), usually defined in a class, that can be used outside the class and in other parts of the program.  

**method** verb used for creating new resources. Because `POST` routes create new data, their paths do not end with a route  

**Preview:** [A parameter is the name of a variable](#) passed into a function. Parameters allow functions to accept inputs. An argument, on the other hand, is the actual value of the variable (also known as the parameter) passed into a function. Suppose we have a function called `tripleThis()`:  
```javascript
function tripleThis(x) {
  return x * 3;
}
tripleThis(6);
```
parameter, but instead end with the type of resource to be created.

For example, to create a new monster, a client would make a POST request to /monsters. The client does not know the id of the monster until it is created and sent back by the server, therefore POST /monsters/:id doesn't make sense because a client couldn't know the unique id of a monster before it exists.

First, we create a new element using createElement() from utils.js:
```javascript
app.post('/monsters', (req, res, next) => {
  const receivedExpression = createElement('monsters', req.query);
```
If our new element is valid, we push() it to our array of elements:
```javascript
monsters.push(receivedExpression);
```
Express uses .post() as its method for POST requests. POST requests can use many ways of sending data to create new resources, including query strings.

The HTTP status code for a newly-created resource is 201 Created.

# Deleting Old Expressions  
**9 min**  

`DELETE` is the HTTP method verb used to delete resources. Because `DELETE` routes delete currently existing data, their paths should usually end with a route parameter to indicate which resource to delete.  

First, we get the index of the resource using `getIndexById()` from `utils.js`:

```javascript
app.delete('/monsters/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, monsters);
```
If the index is valid, we use splice() to remove the element at that index:
```javascript
monsters.splice(expressionIndex, 1);
```
Express uses .delete() as its method for DELETE requests.
Servers often send a 204 No Content status code if deletion occurs without error.

# Adding Animals Routes  
**18 min**  

Congratulations, you have made our glorious Express Yourself Machine fully operational! Not only that, you now have all the tools you need to create a basic CRUD API! Time to practice your skills with a new set of routes.  

You are going to add an additional set of functionality to our machine: Animal Mode! This will involve creating similar `GET`, `POST`, `PUT`, and `DELETE` routes.

```javascript
const express = require('express');
const app = express();

// Serves Express Yourself website
app.use(express.static('public'));

const { getElementById, getIndexById, updateElement,
        seedElements, createElement } = require('./utils');

const expressions = [];
seedElements(expressions, 'expressions');
const animals = [];
seedElements(animals, 'animals');

const PORT = process.env.PORT || 4001;

app.get('/expressions', (req, res, next) => {
  res.send(expressions);
});

app.get('/expressions/:id', (req, res, next) => {
  const foundExpression = getElementById(req.params.id, expressions);
  if (foundExpression) {
    res.send(foundExpression);
  } else {
    res.status(404).send();
  }
});

app.put('/expressions/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    updateElement(req.params.id, req.query, expressions);
    res.send(expressions[expressionIndex]);
  } else {
    res.status(404).send();
  }
});

app.post('/expressions', (req, res, next) => {
  const receivedExpression = createElement('expressions', req.query);
  if (receivedExpression) {
    expressions.push(receivedExpression);
    res.status(201).send(receivedExpression);
  } else {
    res.status(400).send();
  }
});

app.delete('/expressions/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    expressions.splice(expressionIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
});

app.get('/animals', (req, res, next) => {
  res.send(animals);
})

app.get('/animals/:id', (req, res, next) => {
  const foundAnimal = getElementById(req.params.id, animals);
  if (foundAnimal) {
    res.send(foundAnimal);
  } else {
    res.status(404).send();
  }
})

app.put('/animals/:id', (req, res, next) => {
  const animalIndex = getIndexById(req.params.id, animals);
  if (animalIndex !== -1) {
    updateElement(req.params.id, req.query, animals);
    res.send(animals[animalIndex]);
  } else {
    res.status(404).send('Failed to update animal');
  }
});

app.post('/animals', (req, res, next) => {
  const receivedAnimal = createElement('animals', req.query);
  if (receivedAnimal) {
    animals.push(receivedAnimal);
    res.status(201).send(receivedAnimal);
  } else {
    res.status(400).send();
  }
});

app.delete('/animals/:id', (req, res, next) => {
  const animalIndex = getIndexById(req.params.id, animals);
  if (animalIndex !== -1) {
    animals.splice(animalIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
})

app.listen(PORT, () => {
  console.log(`Listening on port ${PORT}`); 
});
```
## Wrap Up
** <1 min **

In this exercise, you were able to create a full server
allowing users to implement all CRUD operations for two kinds of resources: Expressions and Animals! With these skills and knowledge of the HTTP
request-response cycle, you could implement an API
for any project needing CRUD functionality. You could build a trip planner, an address book, a grocery list, an image-sharing application, an anonymous message board, the sky’s the limit!
Continue on to the next lesson to learn more about how to keep your code clean and modular with Express Routers!

# Learn Express Routers

## This File Is Too Big!

**1 min**

Your Expressions/Animals routes are all working well, and our machine is fully functional! Our app.js file, however, is getting quite long and hard to read. It’s easy to imagine that as we add functionality to an application, this file would get long and cumbersome.
Luckily, Express provides functionality to alleviate this problem: Routers. Routers are mini versions of Express applications — they provide functionality for handling route matching, requests, and sending responses, but they do not start a separate server
 or listen on their own ports. Routers use all the `.get()`, `.put()`, `.post()`, and `.delete()` routes that you know and love.
In this lesson, we will use Routers to clean up our code and separate our application into a file to handle all `/expressions routes`, and another to handle all `/animals routes`.

# Express.Router  
**11 min**  

An Express router provides a subset of Express methods. To create an instance of one, we invoke the `.Router()` method on the top-level Express import.

To use a router, we mount it at a certain path using `app.use()` and pass in the router as the second argument. This router will now be used for all paths that begin with that path segment. To create a router to handle all requests beginning with `/monsters`, the code would look like this:

```javascript
const express = require('express');
const app = express();

const monsters = {
  '1': {
    name: 'godzilla',
    age: 250000000
  },
  '2': {
    name: 'manticore',
    age: 21
  }
}

const monstersRouter = express.Router();

app.use('/monsters', monstersRouter);

monstersRouter.get('/:id', (req, res, next) => {
  const monster = monsters[req.params.id];
  if (monster) {
    res.send(monster);
  } else {
    res.status(404).send();
  }
});
```
Inside the `monstersRouter`, all matching routes are assumed to have `/monsters` prepended, as it is mounted at that path`. monstersRouter.get('/:id')` matches the full path `/monsters/:id.`

When a `GET /monsters/1` request arrives:

- Express matches /monsters in `app.use()` because the beginning of the path `('/monsters')` matches

- Express' route-matching algorithm enters the `monstersRouter's routes` to search for full path matches

- Since `monstersRouter.get('/:id')` is mounted at `/monsters`, the two paths together match the entire request path `(/monsters/1)`

- The route matches and the callback is invoked

- The 'godzilla' monster is fetched from the monsters object and sent back.

# Exercise: Using Multiple Router Files  
**11 min**  

Generally, we will keep each router in its own file, and require them in the main application. This allows us to keep our code clean and our files short.

To do this with `monstersRouter`, we would create a new file `monsters.js` and move all code related to `/monsters` requests into it.

```javascript
// monsters.js
const express = require('express');
const monstersRouter = express.Router();

const monsters = {
  '1': {
    name: 'godzilla',
    age: 250000000
  },
  '2': {
    Name: 'manticore',
    age: 21
  }
}

monstersRouter.get('/:id', (req, res, next) => {
  const monster = monsters[req.params.id];
  if (monster) {
    res.send(monster);
  } else {
    res.status(404).send();
  }
});

module.exports = monstersRouter;
```
This code contains all the monsters specific code. In a more full-fledged API, this file would contain multiple routes. To use this router in another file, we use `module.exports` so that other files can access `monstersRouter`. The only other new line of code required is that Express must be required in each file, since we'll need to create a router with `express.Router()`.

Our `main.js` file could then be refactored to import the `monstersRouter`:

```javascript
// main.js
const express = require('express');
const app = express();
const monstersRouter = require('./monsters.js');

app.use('/monsters', monstersRouter);
```
In this example, the `monstersRouter` is required in `main.js` from `monsters.js` and used exactly as it was before.
```javascript
const express = require('express');
const app = express();

const { getElementById, getIndexById, updateElement,
  seedElements, createElement } = require('./utils');

const PORT = process.env.PORT || 4001;
// Use static server to serve the Express Yourself Website
app.use(express.static('public'));

// const expressions = [];
// seedElements(expressions, 'expressions');
const animals = [];
seedElements(animals, 'animals');

const expressionsRouter = require('./expressions.js')
app.use('/expressions', expressionsRouter);

// Get a single expression
app.get('/expressions/:id', (req, res, next) => {
  const foundExpression = getElementById(req.params.id, expressions);
  if (foundExpression) {
    res.send(foundExpression);
  } else {
    res.status(404).send();
  }
});

// Update an expression
app.put('/expressions/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    updateElement(req.params.id, req.query, expressions);
    res.send(expressions[expressionIndex]);
  } else {
    res.status(404).send();
  }
});

// Create an expression
app.post('/expressions', (req, res, next) => {
  const receivedExpression = createElement('expressions', req.query);
  if (receivedExpression) {
    expressions.push(receivedExpression);
    res.status(201).send(receivedExpression);
  } else {
    res.status(400).send();
  }
});

// Delete an expression
app.delete('/expressions/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    expressions.splice(expressionIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
});

// Get all animals
app.get('/animals', (req, res, next) => {
  res.send(animals);
});

// Get a single animal
app.get('/animals/:id', (req, res, next) => {
  const animal = getElementById(req.params.id, animals);
  if (animal) {
    res.send(animal);
  } else {
    res.status(404).send();
  }
});

// Create an animal
app.post('/animals', (req, res, next) => {
  const receivedAnimal = createElement('animals', req.query);
  if (receivedAnimal) {
    animals.push(receivedAnimal);
    res.status(201).send(receivedAnimal);
  } else {
    res.status(400).send();
  }
});

// Update an animal
app.put('/animals/:id', (req, res, next) => {
  const animalIndex = getIndexById(req.params.id, animals);
  if (animalIndex !== -1) {
    updateElement(req.params.id, req.query, animals);
    res.send(animals[animalIndex]);
  } else {
    res.status(404).send();
  }
});

// Delete a single animal
app.delete('/animals/:id', (req, res, next) => {
  const animalIndex = getIndexById(req.params.id, animals);
  if (animalIndex !== -1) {
    animals.splice(animalIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
});

app.listen(PORT, () => {
  console.log(`Server is listening on ${PORT}`);
});
```
```javascript
const express = require('express');
const { seedElements } = require('./utils');
const expressionsRouter = express.Router();

const expressions = [];
seedElements(expressions, 'expressions');

// Get all expressions
expressionsRouter.get('/', (req, res, next) => {
  res.send(expressions);
});

module.exports = expressionsRouter;
```
# Matching In Nested Routers  
**3 min**  

As you saw in the previous exercise, when using routers, it's important to remember that the full path of a request can be segmented.

In the provided diagram, you can see an Express application using two routers. A `GET` request arrives for `/expressions/1`. Because the beginning of the path does not match `/animals` in the first `app.use()`, the Express server moves on to the next `app.use()`, which matches `/expressions`.

Express's route matching algorithm then enters the `expressionsRouter` instance which is required from `expressions.js`. Inside this router, the path matching changes. Even though the whole request path is `/expressions/1`, inside the `expressionsRouter`, all paths are matched from the parts of the path after `/expressions`, meaning that in this context, the router is trying to match the path `/1`.

Because the path is `/1`, the path does not match the first `.get()` method at `/`. The Express server moves on to the next route, which has a route parameter of `/:id`, so it matches! This route handles the necessary logic and sends the response.

Routers can be nested as many times as necessary for an application, so understanding nested route matching is important for creating complicated APIs.

![image](https://github.com/user-attachments/assets/7a61aedc-ae03-40b8-90dc-20f82fcd798c)


# Refactoring Expressions Routes  
**5 min**  

Now that you've learned about nested route matching, let's refactor the rest of the `/expressions` routes into `expressions.js`.

## Instructions  
1. Move all your `/expressions` routes to your router into `expressions.js`. Make sure that they still match the same request paths, and remove the duplicate code from `app.js`.  
2. Move the following routes to `expressions.js`:  
   - `GET /expressions/:id`  
   - `PUT /expressions/:id`  
   - `POST /expressions`  
   - `DELETE /expressions/:id`  
3. Remember to change the paths for each route handler as you move them, as they should already be mounted at `/expressions` inside `expressions.js`.  
4. Make sure that you still require the same helper functions from `utils.js` in `expressions.js`.  

### Refactored app.js
```javascript
const express = require('express');
const app = express();

const { getElementById, getIndexById, updateElement,
  seedElements, createElement } = require('./utils');

const PORT = process.env.PORT || 4001;
// Use static server to serve the Express Yourself Website
app.use(express.static('public'));

let animals = [];
seedElements(animals, 'animals');

const expressionsRouter = require('./expressions.js');

app.use('/expressions', expressionsRouter);

// Get all animals
app.get('/animals', (req, res, next) => {
  res.send(animals);
});

// Get a single animal
app.get('/animals/:id', (req, res, next) => {
  const animal = getElementById(req.params.id, animals);
  if (animal) {
    res.send(animal);
  } else {
    res.status(404).send();
  }
});

// Create an animal
app.post('/animals', (req, res, next) => {
  const receivedAnimal = createElement('animals', req.query);
  if (receivedAnimal) {
    animals.push(receivedAnimal);
    res.status(201).send(receivedAnimal);
  } else {
    res.status(400).send();
  }
});

// Update an animal
app.put('/animals/:id', (req, res, next) => {
  const animalIndex = getIndexById(req.params.id, animals);
  if (animalIndex !== -1) {
    updateElement(req.params.id, req.query, animals);
    res.send(animals[animalIndex]);
  } else {
    res.status(404).send();
  }
});

// Delete a single animal
app.delete('/animals/:id', (req, res, next) => {
  const animalIndex = getIndexById(req.params.id, animals);
  if (animalIndex !== -1) {
    animals.splice(animalIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
});

app.listen(PORT, () => {
  console.log(`Server is listening on ${PORT}`);
});
```
Refactored expressions.js
```javascript
const express = require('express');
const { seedElements, getElementById, createElement, updateElement, getIndexById } = require('./utils');

let expressions = [];
seedElements(expressions, 'expressions');

const expressionsRouter = express.Router();

// Get all expressions
expressionsRouter.get('/', (req, res, next) => {
  res.send(expressions);
});

// Get a single expression
expressionsRouter.get('/:id', (req, res, next) => {
  const foundExpression = getElementById(req.params.id, expressions);
  if (foundExpression) {
    res.send(foundExpression);
  } else {
    res.status(404).send();
  }
});

// Update an expression
expressionsRouter.put('/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    updateElement(req.params.id, req.query, expressions);
    res.send(expressions[expressionIndex]);
  } else {
    res.status(404).send();
  }
});

// Create an expression
expressionsRouter.post('/', (req, res, next) => {
  const receivedExpression = createElement('expressions', req.query);
  if (receivedExpression) {
    expressions.push(receivedExpression);
    res.status(201).send(receivedExpression);
  } else {
    res.status(400).send();
  }
});

// Delete an expression
expressionsRouter.delete('/:id', (req, res, next) => {
  const expressionIndex = getIndexById(req.params.id, expressions);
  if (expressionIndex !== -1) {
    expressions.splice(expressionIndex, 1);
    res.status(204).send();
  } else {
    res.status(404).send();
  }
});

module.exports = expressionsRouter;
```
## Routers Review
**<1 min**

Great job—you created a much more readable and clean code base using Express.Router(). Writing clean and readable code is one of the most important skills as a developer. This will make adding new features much easier as your APIs expand!

# Setting Up Postman  
Get Postman setup on your computer so that you can start testing API requests with ease.

## The Postman App  
Postman is a GUI that aids in the development of APIs by making it easy to test requests and their responses in an organized way. Everything you can do in Postman you can also do through the command line, but Postman makes the process quicker and easier by providing a clean interface and powerful set of tools.

## Download/Installation  
You can download the App for free at [Get Postman](https://www.postman.com/downloads/). Choose the package for your operating system, and then unzip it to install.

## Setting up our Example Backend  
We have created a simple backend that you can interact with to get comfortable with making HTTP requests. This backend uses a SQLite database to store users. Each user has only a username (String) and a password (String). For now, we only have the GET and POST requests set up.

Follow these steps to get the example backend set up:

1. Download the example backend directory [here](#) (link placeholder).
2. Unzip the file.
3. Navigate into the directory through your command line (use `cd example_backend` from whichever directory you unzipped it into).
4. Make sure you have Node installed. To check, you can run `npm -v` on your command line. If you see a version number, you have Node. If the `npm` command is not found, you should follow [these steps](https://nodejs.org/en/download/) to install Node.
5. Run `npm install` from inside the `example_backend` directory to install all of the project's dependencies.

If you run into any npm or gyp errors, try running the following commands to update and re-install any npm packages:

```bash
npm install -g npm-check-updates
npm-check-updates -u
npm install
```
6. To start the server, run `node server.js` from inside the `example_backend` directory. Now, this simple server should be running at `http://localhost:4000`.
# Making GET Requests with Postman
With the example backend running at localhost:4000, open the Postman App. You should see an interface that looks like this:

![image](https://github.com/user-attachments/assets/407203a0-7743-45b6-81ef-ddfe2d7eb4aa)

At the top of the window, you can see a dropdown that lets you choose what kind of HTTP operation to perform. By default, it is set to GET. If you expand the dropdown, you will see all of the possible HTTP methods you can use to interact with this system:
![image](https://github.com/user-attachments/assets/d1bcfb70-cbb5-4582-b653-cbc036c3cc60)
To see all of the users that are currently in the database, make a GET request to localhost:4000/users. To do this, you should:
1.	Make sure the dropdown is set to GET.
2.	Enter the URL localhost:4000/users in the textbox that says “Enter request URL”.
When the you have entered this information, press the Send button:
![image](https://github.com/user-attachments/assets/896ce01a-c180-4295-9062-ce5bd150a457)
The body of the response will appear in the panel at the bottom of the window. You should see two users stored, each with a unique id:

```javascript
{
    "users": [
        {
            "id": 1,
            "username": "1lameuser",
            "password": "secret_password"
        },
        {
            "id": 2,
            "username": "cool_user_87",
            "password": "notPassword!"
        }
    ]
}
```
This tells us that there are currently two users stored in the database. One has a username with the value “1lameuser” and a password with the value “secret_password”, and the other has a username with the value “cool_user_87” and a password with the value “notPassword!”.
We can also GET a specific user by specifying an id in the URL of the GET request. To get the user “1lameuser”, for example, we can send this GET request: localhost:4000/users/1. The response to this request should be:

```javascript
{
    "user": {
        "id": 1,
        "username": "1lameuser",
        "password": "secret_password"
    }
}
```
These GET requests only retrieved resources from the server. No information was changed. Next, we’ll look at how to use Postman to send requests to add users to the system.
# Making POST Requests with Postman

We can use POST requests to add users to the database. Let's practice with sending some POST requests.

## Steps to Make a POST Request:

1. **Change the request type**:
   - Use Postman's dropdown selector to change from `GET` to `POST`

2. **Set the request URL**:
   - Enter `http://localhost:4000/users` in the address bar

3. **Configure the request body**:
   - Select the "Body" tab
   - Check the "raw" radio button
   - Set the format to JSON:
     - Click the dropdown that says "Text"
     - Select "JSON (application/json)"

4. **Enter your JSON payload**:
```json
{
    "username": "new_user_example",
    "password": "securepassword123"
}
```
## Expected Response:

After sending, you should receive a response similar to:
```javascript
{
    "id": 3,
    "username": "new_user_example",
    "password": "securepassword123"
}
```
![image](https://github.com/user-attachments/assets/7a8c0d4f-17b3-48b1-94be-85f5390db72e)

## 5. Creating the Request Body

In the text input field underneath the radio buttons, enter your user object in the required JSON format:

```json
{
    "user": {
        "username": "<your_username>",
        "password": "<your_password>"
    }
}
```
Here is an example of what the interface will look like before you send the request:
![image](https://github.com/user-attachments/assets/0ac1e1c5-cbc5-4fe5-8433-9c7481bcfbe2)
6. 6.	Press the Send button to send the POST request.

Look at the output. What is contained in the response body? Is this what you would expect? For the above example, the output in the response body looks like:

## Successful POST Response Example

After sending a valid POST request to `/users`, you should receive a response similar to:

```json
{
    "user": {
        "id": 3,
        "username": "wholeNewUser",
        "password": "IllNeverTell"
    }
}
```


# Express Routes Code Challenges

## Code Challenge (1 min)

Require the 'express' package and save it to a variable named `express`. Then, create an Express instance and save it to a variable called `app`.

Start your server listening on the port defined by the `PORT` variable.

## Code Challenges

1. Write a `GET /sausages` route that sends back the whole `sausageTypes` array.

2. Fix the route so that it sends back the array of metal building materials.

3. Complete the `GET /battlefields/:name` route. Send back the battlefield object if a battlefield exists, and set the status to 404 and send an empty response if it does not.

4. Write a route to handle `PUT` requests to `/currencies/:name/countries`.
   - The `:name` param represents the currency name in the `currencies` object.
   - The updated array of countries that use this currency will be sent in a query.
   - This route handler should replace the `countries` array of the correct single-currency object with an updated array from the query.
   - It should send the updated array as a response.

5. Create a `POST /soups` route.
   - It should add a new soup name to the `soups` array from the `name` property of the `req.query` object.
   - It should also set a status code for 'Created'.

6. Write a route to handle `DELETE` requests to `/puddings/:flavor`.
   - It should delete the correct pudding and send a 204 response if the pudding name exists.
   - Send a 404 response if it does not.
   - You can use the helper functions `findPuddingIndex` to find the index of the pudding by flavor and `deletePuddingAtIndex` to delete a pudding from the `puddingFlavors` array by index.

7. Mount the `sauceRouter` with `app.use` so that a `GET /sauces` request sends back the `sauces` array.

```javascript
const express = require('express');
const app = express();

const PORT = process.env.PORT || 4001;

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});

const pastas = ['agnolotti', 'cavatelli', 'gemelli', 'tortellini'];

app.get('/pastas', (req, res, next) => {
  res.send(pastas);
});

const sauceRouter = express.Router();
// Add your code here:
app.use('/sauces', sauceRouter);

const sauces = ['carbonara', 'primavera', 'bolognese', 'puttanesca', 'fra diavolo']

sauceRouter.get('/', (req, res, next) => {
  res.send(sauces);
});
```
8. Create two routers - mountainsRouter and mountainRangesRouter. Mount them at /mountains and /mountain-ranges, respectively.

- Create a route handler with mountainsRouter to send back the mountains array in response to a GET /mountains request.

- Create a route handler with mountainRangesRouter to send back the mountainRanges array in response to a GET /mountain-ranges request.


# Quote API

## Overview
This project is slightly different than others you have encountered thus far on Codecademy. Instead of a step-by-step tutorial, this project contains a series of open-ended requirements which describe the project you'll be building. There are many possible ways to correctly fulfill all of these requirements, and you should expect to use the internet, Codecademy, and other resources when you encounter a problem that you cannot easily solve.

## Project Goals
In this project, you'll be building a small Express.js web API to store and serve different quotes about computers, coding, and technology.

## Setup Instructions
If you choose to do this project on your computer instead of Codecademy, you can download what you'll need by clicking the "Download" button below. You'll need to open and work in `server.js` in a text editor. To edit `server.js`, use your text editor of choice. If you need a recommendation or help to install an editor, we recommend looking into our article about setting up a text editor for web development (Follow along until you get to the section: "Practice: Let's Make a Project"). To run your API on your computer, you will need to install Node.js. If you need help installing Node.js, read our article on installing Node.

Once you have an editor an Node.js set up, download the project, unzip it, navigate to that folder in your terminal and run `npm install` to install Express before trying to start up your server.

[Download](#)

## Tasks
8/8 complete
Mark the tasks as complete by checking them off

### Prerequisites
1. [x] To complete this project, you should have completed the Express Routes and Express Routers lessons from our Learn Express curriculum.

### Project Requirements
2. [x] You've been given some starter code in the form of a front-end site and some Express.js boilerplate. You'll use this to build several route handlers to serve up interesting quotes. As you build out your app, test out the functionality either using our front-end or with a tool like Postman. Make sure to re-run `node server.js` as you make changes to the server, and visit `localhost:4001` in the browser to interact with the front-end.

   As you work, your server at any point with Ctrl + C in the terminal, and then restart it to see new changes in its behavior.

   In `server.js`, we've provided you with some imported helper functions and data:
   - A `quotes` array with some pre-populated quotes about technology. Each quote in the array has a `person` and `quote` property. You can use our array or write your own, but make sure to have at least the `person` and `quote` properties, as the front-end that we've provided expects each quote to have them.
   - The `getRandomElement()` function, which takes an array and returns a random element from that array.

3. [x] Set your server to listen on the `PORT` variable.
   
   Once you start up the server with `node server.js`, navigate to `localhost:4001` in the browser. You'll know things are up and running when you load the blue Quote API site in the browser.

   This diagram explains how the front-end buttons correspond to different request routes.

4. [x] Your API should have a `GET /api/quotes/random` route. This route should send back a random quote from the quotes data. The response body should have the following shape:
   ```json
   {
     "quote": {/* quote object */}
   
   ```
5. [x] Your API should have a GET /api/quotes route. This route should return all quotes from the data if the request has no query params.

If there is a query string with a person attribute, the route should return all quotes said by the same person. For instance, the data set has multiple quotes for Grace Hopper, so GET /api/quotes?person=Grace Hopper should return an array of only those quotes. If there are no quotes for the requested person, send back an empty array.

The response body should have the following shape for all GET /api/quotes requests:
```javascript
{
  "quotes": [ /* Array of requested quotes */ ]
}
```
6. [x] Your API should have a POST /api/quotes route for adding new quotes to the data. New quotes will be passed in a query string with two properties: quote with the quote text itself, and person with the person who is credited with saying the quote.

This route should verify that both properties exist in the request query string and send a 400 response if it does not. If all is well, this route handler should add the new quote object to the data array and send back a response with the following shape:
```javascript
{
  "quote": {/* new quote object */}
}
```
## Solution Code & Extensions
7. [x] Great work! Visit our forums to compare your project to our sample solution code. You can also learn how to host your own solution on GitHub so you can share it with other learners! Your solution might look different from ours, and that's okay! There are multiple ways to solve these projects, and you'll learn more by seeing others' code.

8. [x] If you'd like to extend your app, here are some ideas to try, but you can also try out your own:

- Add a PUT route for updating quotes in the data. This might require adding some sort of unique ID for each quote in the array in data.js.

- Add a DELETE route for deleting quotes from the data array. As with PUT, this might require adding IDs to the data array and using req.params. For both of these ideas, you'll be able to interact via Postman.

- Add other data to the array, such as the year of each quote, and try to display it on the front-end.

- Add another resource to your API in addition to quotes, such as biographical blurbs (you'll need to find your own data for this new resource). Use Express Routers to keep your code simple and separated into different files for each router.

For most of these ideas, you might need to look into the front-end code in the public/ folder. If you're not as familiar with front-end JavaScript, try our Build Interactive JavaScript Websites course and the Requests section of our Introduction to JavaScript course.

# Middleware

## Introduction

**1 min**

Writing code is a creative process. Programmers will be quick to differ in opinion on whether the solution to a problem should be implemented in one way or another — citing tradeoffs in algorithms, structures, or even languages. Due to these trade-offs, the problems programmers face most frequently will have several different solutions, all correct but all written differently with various factors considered. Because “correct” code can take so many different forms, developers have cultural notions of code quality that is somewhat independent of these decisions.
One concept that is central to the notion of quality code is that all code is read many, many more times than it is written. Maintaining and updating code takes up much more of a software developer’s time than production. There are many ways to make this less of a burden, and these techniques frequently correspond to code quality principles. Naming variables
 consistently so that they’re identifiable is one way to improve the readability of a codebase. Another pillar of code quality is avoiding duplication of code within a codebase.
Code duplication is an invitation for bugs. If incorrect code is copy-and-pasted in multiple places, a developer might remedy the flaws in only a few of those places and fail to fix the buggy code everywhere. In this course, we will investigate several ways to avoid replication and reduce complexity. In programming in general, this often means putting the reused code into reusable containers like functions and objects. In Express specifically, this will also mean composing our desired functionality into a series of middleware functions.


# DRYing Code With Functions  
**11 min**  

Beyond labeling, good code will leverage the strength of its programming language to avoid performing the same tasks.  

Take a look at the following code:  

```javascript
const addFive = number => {
  const fiveAdded = number + 5;
  console.log(`Your number plus 5 is ${fiveAdded}`);
}

const addTen = number => {
  const tenAdded = number + 10;
  console.log(`Your number plus 10 is ${tenAdded}`);
}

const addTwenty = number => {
  const twentyAdded = number + 20;
  console.log(`Your number plus 20 is ${twentyAdded}`);
}
```
While these three function definitions are not exact duplicates of each other, a well-designed application will be flexible enough to join similar functionality in a single element.
```javascript
const addNumber = (number, addend) => {
  const numAdded = number + addend;
  console.log(`Your number plus ${addend} is ${numAdded}`);
}
```
As you can see, by adding an argument to the earlier functions, we can simplify our application code, which will ultimately save time should we realize that we also want an addFifty() function and an addHundred() function.

Code that performs the same task in multiple places is repetitive, and the quality coder’s credo is “Don’t Repeat Yourself” (DRY). If a program performs similar tasks without refactoring into a function, it is said to “violate DRY”.

“Violating DRY” is a programmer’s way of complaining:

“This script is saying the same thing over and over! We can do the same thing with less code!”

Let’s try to not repeat ourselves in this codebase by repurposing some of the more glaringly repeated code into functions we can call instead.

# DRYing Routes With app.use()

**9 min**

By now you may have noticed that our efforts to not repeat ourselves have resulted in us putting the same function call over and over throughout our code. Isn't that somewhat contradictory? You would be absolutely right to think so.

So how do we get code to run every time one of our Express routes is called without repeating ourselves? We write something called 

> **Preview:** Docs Middleware is software that connects data, APIs, software tools, and other applications in order to bring a complete application to the end user.

**middleware**. Middleware is code that executes between a server receiving a request and sending a response. It operates on the boundary, so to speak, between those two HTTP actions.

In Express, middleware is a function. Middleware can perform logic on the request and response objects, such as: inspecting a request, performing some logic based on the request, attaching information to the response, attaching a status to the response, sending the response back to the user, or simply passing the request and response to another middleware. Middleware can do any combination of those things or anything else a Javascript function can do.

```javascript
app.use((req, res, next) => {
  console.log('Request received');
});
```
The previous code snippet is an example of middleware in action. app.use() takes a callback function that it will call for every received request. In this example, every time the server receives a request, it will find the first registered middleware function and call it. In this case, the server will find the callback function specified above, call it, and print out 'Request received'.

You might be wondering what else our application is responsible for that isn't related to middleware. The answer is not much. To quote the Express documentation:

An Express application is essentially a series of middleware function calls.

It is precisely this service that we leverage Express for. In addition to performing the routing that allows us to communicate appropriate data for each separate endpoint, we can perform application logic we need by implementing the necessary middleware.


## next()

**5 min**

It seems like our middleware was successful — it logged out the type of each request received. But then the response stopped there! What happened? We mentioned that most of Express’s functionality is chaining middleware. This chain of middleware is referred to as the **middleware stack**.

The middleware stack is processed in the order they appear in the application file, such that middleware defined later happens after middleware defined before. It’s important to note that this is regardless of method — an `app.use()` that occurs after an `app.get()` will get called after the `app.get()`. Observe the following code:

```javascript
app.use((req, res, next) => {
  console.log("A sorcerer approaches!");
  next();
});

app.get('/magic/:spellname', (req, res, next) => {
  console.log("The sorcerer is casting a spell!");
  next();
});

app.get('/magic/:spellname', (req, res, next) => {
  console.log(`The sorcerer has cast ${req.params.spellname}`);
  res.status(200).send();
});

app.get('/magic/:spellname', (req, res, next) => {
  console.log("The sorcerer is leaving!");
});
```
Accessing `http://localhost:4001/magic/fireball`
Console Output:

"A sorcerer approaches!"
"The sorcerer is casting a spell!"
"The sorcerer has cast fireball"

in the above code, the routes are called in the order that they appear in the file, provided the previous route called next() and thus passed control to the next middleware. We can see that the final matching call was not printed. This is because the previous middleware did not invoke the next() function to run the following middleware.

An Express middleware is a function with three parameters: (req, res, next). The sequence is expressed by a set of callback functions invoked progressively after each middleware performs its purpose. The third argument to a middleware function, next, should get explicitly called as the last part of the middleware’s body. This will hand off the processing of the request and the construction of the response to the next middleware in the stack.

# Request And Response Parameters

**1 min**

Recall the function signature of an Express middleware, i.e., (req, res, next). You might recognize this signature as being the very same that we’ve used for Express routes in the past. Well there’s a perfectly good reason for that: Express routes are middleware. Every route created in Express is also a middleware function handling the request and response objects at that part of the stack. Express routes also have the option of sending a response body and status code and closing the connection. These two features are a byproduct of Express routes being middleware, because all Express middleware functions have access to the request, the response, and the next middleware in the stack.

# Route-Level `app.use()` - Single Path  
**19 min**  

Now that we’ve managed to refactor our duplicate code into middleware functions, we should be noticing that our code contains much less repetition than before. Unfortunately, we still have duplicate code in some of our routes. Since this code isn’t shared by all of our routes, the previous syntax of `app.use()` won’t work. Let’s see what the Express documentation for `app.use()` has to say about this use case. This is the `app.use()` function signature:  

```javascript
app.use([path,] callback [, callback...])
```
In documentation for many programming languages, optional arguments for functions are placed in square brackets ([]). This means that app.use() takes an optional path parameter as its first argument. We can now write middleware that will run for every request at a specific path.
```javascript
app.use('/sorcerer', (req, res, next) => {
  console.log('User has hit endpoint /sorcerer');
  next();
});
```
In the example above the console will print 'User has hit endpoint /sorcerer', if someone visits our web page’s ‘/sorcerer’ endpoint. Since the method
app.use() was used, it won’t matter if the user is performing a GET,a POST, or any other kind of HTTP request. Since the path was given as an argument to app.use(), this middleware function will not execute if the user hits a different path (for instance: '/spells' or '/sorcerer/:sorcerer_id').

# Control Flow With next()
**3 min**

We’ve experienced writing middleware that performs its function and hands off the request and response objects to the next function in the stack, but why exactly do we have to write next() at the end of every middleware? If it always needs to be at the end of every function we write, it seems like an unnecessary piece of boilerplate. You might be surprised to learn that we aren’t going to introduce a way to automatically hand off the request and response objects without having to repeatedly write next(). Rather, we’re going to explore why it is useful to have next() as a separate function call. The biggest reason being we don’t always want to pass control to the next middleware in the stack.
For example, when designing a system with confidential information, we want to be able to selectively show that information to authorized users. In order to do that, we would create middleware that tests a user’s permissions. If the user has the permission necessary, we would continue through the middleware stack by calling next(). If it fails, we would want to let the user know that they’re not allowed to see the information they’re trying to access.

# Route-Level app.use() - Multiple Paths
**17 min**

We learned that `app.use()` takes a path parameter, but we never fully investigated what that path parameter could be. Let's take another look at the Express documentation for `app.use()`:

> "argument: path  
> description: The path for which the middleware function is invoked; can be any of:  
> • A string representing a path.  
> • A path pattern.  
> • A regular expression pattern to match paths.  
> • An array of combinations of any of the above."

So `app.use()` can take an array of paths! That seems like a handy way to rewrite the code from our last exercise so that we don't have to put the same code in two different routes with different paths.

```javascript
const express = require("express");
const app = express();

app.use(express.static("public"));

const PORT = process.env.PORT || 4001;

const jellybeanBag = {
  mystery: {
    number: 4,
  },
  lemon: {
    number: 5,
  },
  rootBeer: {
    number: 25,
  },
  cherry: {
    number: 3,
  },
  licorice: {
    number: 1,
  },
};

// Logging Middleware
app.use((req, res, next) => {
  console.log(`${req.method} Request Received`);
  next();
});

app.use("/beans/:beanName", (req, res, next) => {
  const beanName = req.params.beanName;
  if (!jellybeanBag[beanName]) {
    console.log("Response Sent");
    return res.status(404).send("Bean with that name does not exist");
  }
  req.bean = jellybeanBag[beanName];
  req.beanName = beanName;
  next();
});

// Add your code below:
app.use(["/beans/", "/beans/:beanName"], (req, res, next) => {
  let bodyData = "";
  req.on("data", (data) => {
    bodyData += data;
  });
  req.on("end", () => {
    if (bodyData) {
      req.body = JSON.parse(bodyData);
    }
  });
  next();
});

app.get("/beans/", (req, res, next) => {
  res.send(jellybeanBag);
  console.log("Response Sent");
});

app.post("/beans/", (req, res, next) => {
  let bodyData = "";
  req.on("data", (data) => {
    bodyData += data;
  });

  req.on("end", () => {
    const body = JSON.parse(bodyData);
    const beanName = body.name;
    if (jellybeanBag[beanName] || jellybeanBag[beanName] === 0) {
      return res.status(400).send("Bean with that name already exists!");
    }
    const numberOfBeans = Number(body.number) || 0;
    jellybeanBag[beanName] = {
      number: numberOfBeans,
    };
    res.send(jellybeanBag[beanName]);
    console.log("Response Sent");
  });
});

app.get("/beans/:beanName", (req, res, next) => {
  res.send(req.bean);
  console.log("Response Sent");
});

app.post("/beans/:beanName/add", (req, res, next) => {
  let bodyData = "";
  req.on("data", (data) => {
    bodyData += data;
  });

  req.on("end", () => {
    const numberOfBeans = Number(JSON.parse(bodyData).number) || 0;
    req.bean.number += numberOfBeans;
    res.send(req.bean);
    console.log("Response Sent");
  });
});

app.post("/beans/:beanName/remove", (req, res, next) => {
  let bodyData = "";
  req.on("data", (data) => {
    bodyData += data;
  });

  req.on("end", () => {
    const numberOfBeans = Number(JSON.parse(bodyData).number) || 0;
    if (req.bean.number < numberOfBeans) {
      return res.status(400).send("Not enough beans in the jar to remove!");
    }
    req.bean.number -= numberOfBeans;
    res.send(req.bean);
    console.log("Response Sent");
  });
});

app.delete("/beans/:beanName", (req, res, next) => {
  const beanName = req.params.beanName;
  if (!req.bean) {
    return res.status(404).send("Bean with that name does not exist");
  }
  req.bean = null;
  res.status(204).send();
  console.log("Response Sent");
});

app.put("/beans/:beanName/name", (req, res, next) => {
  const beanName = req.params.beanName;
  if (!req.bean) {
    return res.status(404).send("Bag with that name does not exist");
  }
  let bodyData = "";
  req.on("data", (data) => {
    bodyData += data;
  });

  req.on("end", () => {
    const newName = JSON.parse(bodyData).name;
    jellybeanBag[newName] = req.bean;
    req.bean = null;
    res.send(jellybeanBag[newName]);
    console.log("Response Sent");
  });
});

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```
# Middleware Stacks  
**11 min**  

Recall that middleware is just a function with a specific signature, namely `(req, res, next)`. We have, for the most part, been using anonymous function definitions for this because our middleware has only been relevant to the route invoking it. There is nothing stopping us from defining functions and using them as middleware though. That is to say:  

```javascript
const logging = (req, res, next) => {
  console.log(req);
  next();
};

app.use(logging);
```
is a valid and reasonable way to introduce logging throughout all paths. It is also modifiable so that you can remove the app.use() line and replace it with a specific route method, or sprinkle it throughout the application without it being universal.

Up until this point we’ve only been giving each middleware-accepting method a single callback. With modular pieces like this, it is useful to know that methods such as app.use(), app.get(), app.post(), and so on all can take multiple callbacks as additional parameters. This results in code that looks like the following:

```javascript
const authenticate = (req, res, next) => {
  ...
};

const validateData = (req, res, next) => {
  ...
};

const getSpell = (req, res, next) => {
  res.status(200).send(getSpellById(req.params.id));
};

const createSpell = (req, res, next) => {
  createSpellFromRequest(req);
  res.status(201).send();
};

const updateSpell = (req, res, next) => {
  updateSpellFromRequest(req);
  res.status(204).send();
}

app.get('/spells/:id', authenticate, getSpell);

app.post('/spells', authenticate, validateData, createSpell);

app.put('/spells/:id', authenticate, validateData, updateSpell);
```
In the above code sample, we created reusable middleware for authentication and data validation. We use the authenticate() middleware to verify a user is logged in before proceeding with the request and we use the validateData() middleware before performing the appropriate create or update function. Additional middleware can be placed at any point in this chain.

# Open-Source Middleware: Logging  
**7 min**  

Knowing how to write middleware, we should now feel inspired to solve all the problems that come at us by writing code. It’s encouraging to know how to fix an issue. If we find a solution we don’t need to write, however, it will allow us to work faster and more intelligently to focus on the problems that differentiate our application from others.  

To illustrate: if we needed to write a web  

**Preview: Docs**  
A server is a hardware or software device used to provide resources to clients or requesting applications. Servers run on an architecture for fulfilling requests called the "Client-Server Model", which works by the client asking the server for specific data in an agreed upon format and the server readying and providing the data.  

**server**  

from scratch every time we wanted to build a web application, we’d waste a lot of time solving problems that have been solved countless times before and ignoring perfectly good pre-existing solutions. Luckily for us web developers, Express already exists as an open-source package that we can install and use to build upon. There is a huge ecosystem of Javascript packages that will solve so many of the problems that developers frequently run into.  

In the workspace you’ll see what code looks like using unnecessary custom solutions and lots of lines calling `console.log()`. It’s not bad code, but it introduces complexity that could be avoided. Time spent thinking about and writing code that accomplishes common tasks is time that could be better spent on thinking about and writing code that is unique to your application.  

We will replace the logging code in the workspace with `morgan`, an open-source library for logging information about the HTTP request-response cycle in a server application. `morgan()` is a function that will return a middleware function, to reiterate: the return value of `morgan()` will be a function, that function will have the function signature `(req, res, next)` that can be inserted into an `app.use()`, and that function will be called before all following middleware functions. Morgan takes an argument to describe the formatting of the logging output. For example, `morgan('tiny')` will return a middleware function that does a “tiny” amount of logging. With `morgan` in place, we’ll be able to remove the existing logging code. Once we see how fast it is to add logging with `morgan`, we won’t have to spend time in the future trying to figure out how to replicate that functionality.

# Documentation  
**4 min**  
With software we’ve personally written, invocation is a simple process. We already know what the code does, what it expects, and may have some notion how things could go wrong. Losing this intuition is the biggest downside to using open-source packages.  
This is not meant to be discouraging. The best open-source packages have extremely well written documentation. Documentation is a resource, presented by the package’s author(s), that includes information about what software is, what it does, and how to use it. We’ve seen the Express documentation in this course, and now we’re going to look at the morgan documentation.

## Open-Source Middleware: Body Parsing  
**8 min**  
Being able to use open-source middleware can certainly make our jobs as programmers a lot easier. Not only does it prevent us from having to write the same code every time we want to accomplish a common task, it allows us to perform some tasks that would take a lot of research for us to implement.  
When we implement middleware, we take in the `req` object, so that we can see information about the request. This object includes a good deal of important information about the request that we can use to inform our response, however for some requests it misses a fundamental piece. An HTTP request can include a body, a set of information to be transmitted to the server for processing. This is useful when the end user needs to send information to the server. If you’ve ever uploaded a post onto a social media website or filled out a registration form chances are you’ve sent an HTTP request with a body. The lucky thing about using open-source middleware is that even though parsing the body of an HTTP request is a tricky operation requiring knowledge about network data transfer concepts, we easily manage it by importing a library to do it for us.  
If we look at our `bodyParser`, we see a simplified version of how one might perform request body parsing. Let’s see if there’s a better way that doesn’t involve us trying to create our own body-parser. Maybe we can find a library that does it for us?  
Take a look at `body-parser`. “Node.js body parsing middleware”, that’s just what we needed! Let’s see if we can use this dependency instead of trying to manage our own body-parsing library.  

```javascript
const express = require('express');
const app = express();
const morgan = require('morgan');
const bodyParser = require('body-parser');

app.use(express.static('public'));

const PORT = process.env.PORT || 4001;

const jellybeanBag = {
  mystery: {
    number: 4
  },
  lemon: {
    number: 5
  },
  rootBeer: {
    number: 25
  },
  cherry: {
    number: 3
  },
  licorice: {
    number: 1
  }
};

app.use(bodyParser.json());

// Logging Middleware
app.use(morgan('dev'));

app.use('/beans/:beanName', (req, res, next) => {
  const beanName = req.params.beanName;
  if (!jellybeanBag[beanName]) {
    return res.status(404).send('Bean with that name does not exist');
  }
  req.bean = jellybeanBag[beanName];
  req.beanName = beanName;
  next();
});

app.get('/beans/', (req, res, next) => {
  res.send(jellybeanBag);
});

app.post('/beans/', (req, res, next) => {
  const body = req.body;
  const beanName = body.name;
  if (jellybeanBag[beanName] || jellybeanBag[beanName] === 0) {
    return res.status(400).send('Bean with that name already exists!');
  }
  const numberOfBeans = Number(body.number) || 0;
  jellybeanBag[beanName] = {
    number: numberOfBeans
  };
  res.send(jellybeanBag[beanName]);
});

app.get('/beans/:beanName', (req, res, next) => {
  res.send(req.bean);
});

app.post('/beans/:beanName/add', (req, res, next) => {
  const numberOfBeans = Number(req.body.number) || 0;
  req.bean.number += numberOfBeans;
  res.send(req.bean);
});

app.post('/beans/:beanName/remove', (req, res, next) => {
  const numberOfBeans = Number(req.body.number) || 0;
  if (req.bean.number < numberOfBeans) {
    return res.status(400).send('Not enough beans in the jar to remove!');
  }
  req.bean.number -= numberOfBeans;
  res.send(req.bean);
});

app.delete('/beans/:beanName', (req, res, next) => {
  const beanName = req.beanName;
  jellybeanBag[beanName] = null;
  res.status(204).send();
});

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```
# Error-Handling Middleware
**12 min**

We’re almost finished with our Code Quality Checklist, there’s just one last problem to fix! When an error is thrown somewhere in our code, we want to be able to communicate that there was a problem to the user. A programming error is never something to be ashamed of. It's simply another situation for which we should be prepared.

Error handling middleware needs to be the last `app.use()` in your file. If an error happens in any of our routes, we want to make sure it gets passed to our error handler. The middleware stack progresses through routes as they are presented in a file, therefore the error handler should sit at the bottom of the file. How do we write it?

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
Based on the code above, we can see that error-handling middleware is written much like other kinds of middleware. The biggest difference is that there is an additional parameter in our callback function, `err`. This represents the error object, and we can use it to investigate the error and perform different tasks depending on what kind of error was thrown. For now, we only want to send an HTTP 500 status response to the user.

Express has its own error-handler, which catches errors that we haven't handled. But if we anticipate an operation might fail, we can invoke our error-handling middleware. We do this by passing an error object as an argument to `next()`. Usually, `next()` is called without arguments and will proceed through the middleware stack as expected. When called with an error as the first argument, however, it will call any applicable error-handling middleware.
```javascript
app.use((req, res, next) => {
  const newValue = possiblyProblematicOperation();
  if (newValue === undefined) {
    let undefinedError = new Error('newValue was not defined!');
    return next(undefinedError);
  }
  next();
});

app.use((err, req, res, next) => {
  const status = err.status || 500;
  res.status(status).send(err.message);
});
```
In this segment we assign the return value of the function `possiblyProblematicOperation()` to newValue. Then we check to see if this function returned anything at all. If it didn't, we create a `newError` and pass it to `next()`. This prompts the error-handling middleware to send a response back to the user, but many other error-handling techniques could be employed (like logging, re-attempting the failed operation, and/or emailing the developer).
```javascript
const express = require('express');
const app = express();
const morgan = require('morgan');
const bodyParser = require('body-parser');

app.use(express.static('public'));

const PORT = process.env.PORT || 4001;

const jellybeanBag = {
  mystery: {
    number: 4
  },
  lemon: {
    number: 5
  },
  rootBeer: {
    number: 25
  },
  cherry: {
    number: 3
  },
  licorice: {
    number: 1
  }
};

// Body-parsing Middleware
app.use(bodyParser.json());

// Logging Middleware
if (!process.env.IS_TEST_ENV) {
  app.use(morgan('dev'));
}

app.use('/beans/:beanName', (req, res, next) => {
  const beanName = req.params.beanName;
  if (!jellybeanBag[beanName]) {
    return res.status(404).send('Bean with that name does not exist');
  }
  req.bean = jellybeanBag[beanName];
  req.beanName = beanName;
  next();
});

app.get('/beans/', (req, res, next) => {
  res.send(jellybeanBag);
});

app.post('/beans/', (req, res, next) => {
  const body = req.body;
  const beanName = body.name;
  if (jellybeanBag[beanName] || jellybeanBag[beanName] === 0) {
    return res.status(400).send('Bean with that name already exists!');
  }
  const numberOfBeans = Number(body.number) || 0;
  jellybeanBag[beanName] = {
    number: numberOfBeans
  };
  res.send(jellybeanBag[beanName]);
});

app.get('/beans/:beanName', (req, res, next) => {
  res.send(req.bean);
});

app.post('/beans/:beanName/add', (req, res, next) => {
  const numberOfBeans = Number(req.body.number) || 0;
  req.bean.number += numberOfBeans;
  res.send(req.bean);
});

app.post('/beans/:beanName/remove', (req, res, next) => {
  const numberOfBeans = Number(req.body.number) || 0;
  if (req.bean.number < numberOfBeans) {
    return res.status(400).send('Not enough beans in the jar to remove!');
  }
  req.bean.number -= numberOfBeans;
  res.send(req.bean);
});

app.delete('/beans/:beanName', (req, res, next) => {
  const beanName = req.beanName;
  jellybeanBag[beanName] = null;
  res.status(204).send();
});

// Add your error handler here:
app.use((err, req, res, next) => {
  const status = err.status || 500;
  res.status(status).send(err.message);
})

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```
# Discovering Open-Source Middleware
**4 min**

While it’s good to know how to write error-handling middleware, it’s a natural curiosity that causes us to ask “isn’t error-handling a common task? Has someone written middleware that performs it for us?” Let’s take a look at the list of Express middleware. This list of middleware includes many things the creators of Express maintain, some of which was included in Express in previous versions. The movement on the Express team’s part to identify separate functionality and modularize their code into independent factors allows developers like us to only take what we need. In this way, they can make major updates to each middleware individually and programmers who do not use that middleware won’t have to worry about their version of Express being out of date.
Can you find something on that list that will help us handle errors?


# Review
**15 min**

We’ve accomplished a lot! We learned what middleware is and we’ve used it to write cleaner, readable, adaptable, and maintainable code. We’ve written functions that are context aware and can have overlapping functionality without duplicating code. We can serve data by route, with each possible endpoint being treated as a separate relative of the family of our application. We learned to link these middleware using next() to continue to the next middleware in the stack. We’ve reduced complexity in our codebase by relying on external, open-source middleware. We are truly harnessing the power of the Express web server, the Node environment, and our knowledge of Javascript. Let’s review those skills.
In the workspace there is another codebase with a set of familiar problems. Custom middleware to accomplish tasks we could be importing a module for. Duplicated code throughout the different routes. Improperly managed middleware stack missing next() calls. You will need everything learned in this lesson, but it’s nothing you haven’t done before.

# Router Parameters
## Introduction
**1 min**

When building interfaces with Express, we will run into the pattern of expecting certain information in a requested URL and using that information to identify the data that is being requested. To give an example:

```javascript
app.get('/sorcerers/:sorcererName', (req, res, next) => {
  const sorcerer = Sorcerers[req.params.sorcererName];
  res.send(sorcerer.info);
});

app.get('/sorcerers/:sorcererName/spellhistory', (req, res, next) => {
  const sorcerer = Sorcerers[req.params.sorcererName];
  const spellHistory = Spells[sorcerer.id].history;
  res.send(spellHistory);
});
```
In the above code we need to extract the request parameter :sorcererName from the url in both instances, and end up duplicating the necessary code so that it appears in both routes. When working with routes that require parameters, we might find ourselves in a position where multiple different routes require the same parameter and use it to identify the same piece of data. While writing this duplicate code will get the job done, copy-and-pasting functionality does leave a bitter taste in the mouth of the principled developer. We should investigate if there is a better way to accomplish this.


### `router.param()`

17 min

Express, luckily, is mindful of the pain-point of replicated parameter-matching code and has a method specifically for this issue. When a specific parameter is present in a route, we can write a function that will perform the necessary lookup and attach it to the `req` object in subsequent middleware that is run.

```javascript
app.param('spellId', (req, res, next, id) => {
  let spellId = Number(id);
    try {
      const found = SpellBook.find((spell) => {
        return spellId === spell.id;
      })
      if (found) {
        req.spell = found;
        next();
      } else {
        next(new Error('Your magic spell was not found in any of our tomes'));
      };
    } catch (err) {
      next(err)
    }
});
```
In the code above we intercept any request to a route handler with the `:spellId` parameter. Note that in the `app.param` function signature, `'spellId'` does not have the leading :. The actual ID will be passed in as the fourth argument, id in this case, to the app.param callback function when a request arrives.

We look up the spell in our `SpellBook` array using the `.find()` method. If SpellBook does not exist, or some other error is thrown in this process, we pass the error to the following middleware (hopefully we've written some error-handling middleware, or included some externally-sourced error-handling middleware). If the spell exists in SpellBook, the .find() method will store the spell in found, and we attach it as a property of the request object (so future routes can reference it via req.spell). If the requested spell does not exist, .find() will store undefined in found, and we let future middlewares know there was an error with the request by creating a new Error object and passing it to next().

Note that inside an `app.param` callback, you should use the fourth argument as the parameter's value, not a key from the `req.params` object.


1. Let’s refactor this code to use `app.param` for all `/spices/:spiceId` routes.
   
   First, start your code with a call to `app.param`. Write functionality that will look for the `spiceIndex` and attach it to the `req` object as `req.spiceIndex` if it exists. Call `next` after that. If it does not exist, send a 404 error response and do not call `next`.

2. Checkpoint 2 Passed

2. Now, refactor your current code to get rid of any index-checking logic in `/spices/:spiceId` routes. Use `req.spiceIndex` to do any necessary operations on the `spiceRack` object. You should also get rid of anything that would send an error response, as non-existent ids will already have been handled by `router.param`.

```javascript
const express = require('express');
const app = express();
const bodyParser = require('body-parser');

app.use(express.static('public'));

const PORT = process.env.PORT || 4001;

const spiceRack = [
  {
    id: 1,
    name: 'cardamom',
    grams: 45,
  },
  {
    id: 2,
    name: 'pimento',
    grams: 20,
  },
  {
    id: 3,
    name: 'cumin',
    grams: 450,
  },
  {
    id: 4,
    name: 'sichuan peppercorns',
    grams: 107,
  }
];

let nextSpiceId = 5;

app.use(bodyParser.json());

// Add your code here:
app.param('spiceId', (req, res, next, id) => {
  const spiceId = Number(id);
  const spiceIndex = spiceRack.findIndex(spice => spice.id === spiceId);
  if (spiceIndex !== -1){
    req.spiceIndex = spiceIndex;
    next();
  } else {
    res.sendStatus(404);
  }
})

app.get('/spices/', (req, res, next) => {
  res.send(spiceRack);
});

app.post('/spices/', (req, res, next) => {
  const newSpice = req.body.spice;
  if (newSpice.name  && newSpice.grams) {
    newSpice.id = nextSpiceId++;
    spiceRack.push(newSpice);
    res.send(newSpice);
  } else {
    res.status(400).send();
  }
});

app.get('/spices/:spiceId', (req, res, next) => {
  res.send(spiceRack[req.spiceIndex]);
});

app.put('/spices/:spiceId', (req, res, next) => {
  spiceRack[req.spiceIndex] = req.body.spice;
  res.send(spiceRack[req.spiceIndex]);
});

app.delete('/spices/:spiceId', (req, res, next) => {
  spiceRack.splice(req.spiceIndex, 1);
  res.status(204).send();
});

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

# Merge Parameters  
**15 min**  

Complexity is all around us. Buildings are made from bricks and many droplets of water make a cloud. When we want to create something complex in software, we model out our base components and use composition to create these relationships.  

When we're building web endpoints, we might want to access some property of a complex object. In order to do this in Express, we can design a nested router. This would be a router that is invoked within another router. In order to pass parameters the parent router has access to, we pass a special configuration object when defining the router.  

```javascript
const sorcererRouter = express.Router();
const familiarRouter = express.Router({mergeParams: true});

sorcererRouter.use('/:sorcererId/familiars', familiarRouter);

sorcererRouter.get('/', (req, res, next) => {
  res.status(200).send(Sorcerers);
  next();
});

sorcererRouter.param('sorcererId', (req, res, next, id) => {
  const sorcerer = getSorcererById(id);   
  req.sorcerer = sorcerer;
  next();
});

familiarRouter.get('/', (req, res, next) => {
  res.status(200).send(`Sorcerer ${req.sorcerer} has familiars ${getFamiliars(sorcerer)}`);
});

app.use('/sorcerer', sorcererRouter);
```
In the code above we define two endpoints: `/sorcerer` and `/sorcerer/:sorcererId/familiars`. The familiars are nested into the sorcerer endpoint — indicating the relationship that a sorcerer has multiple familiars. Take careful note of the `{mergeParameters: true}` argument that gets passed when creating the `familiarRouter`. This argument tells Express that the `familiarRouter` should have access to parameters passed into its parent router, that is, the `sorcererRouter`. We then tell express that the path for the `familiarRouter` is the same as the path for the `sorcererRouter` with the additional path `/:sorcererId/familiars`. We then can create a family of routes (a router) built by appending routes to familiarRouter's base: `/sorcerer/:sorcererId/familiars`.

# Spices API Enhancement

Let's make our spices API more flexible and allow spices to be associated with different spice racks. The goal for this exercise will be to ensure that when new spices are created or updated, they will be associated with the correct spice rack.

In the workspace, you have a new root `app.js` file and a `spicesRouter.js` with code from the last exercise. `app.js` will handle interactions retrieving, creating, updating, and deleting spice racks, and `spicesRouter.js` will be nested to handle individual spices with the spice racks. Each file has a `param` method call (`app.param` in `app.js`, `router.param` in `spicesRouter.js`).

## Implementation Steps

1. **Hook up the router**:  
   At the end of `app.js`, use the `spicesRouter` for all `/spice-racks/:spiceRackId/spices` routes.

2. **Merge parameters**:  
   Make sure that the `spicesRouter` is merging parameters from parent `app.js` Express instance. Add the proper options to the `.Router()` method at the top of your `spicesRouter.js` file.

3. **Associate spices with racks**:  
   Inside your `.post()` route, make sure to set the `newSpice.spiceRackId` equal to the `req.params.spiceRackId` that the parent router attached if `mergeParams` has performed as expected. Don't forget to convert the `spiceRackId` to a number before attaching it. Make sure to set this before it is pushed onto the `spices` array.

## Code Implementation

```javascript
const express = require('express');
const app = express();
const bodyParser = require('body-parser');

app.use(express.static('public'));

const PORT = process.env.PORT || 4001;

app.use(bodyParser.json());

const spiceRacks = [
  {
    id: 1,
    location: 'Kitchen Countertop',
  },
  {
    id: 2,
    location: 'Pantry',
  },
  {
    id: 3,
    location: 'Outdoor Barbecue',
  }
];

let nextSpiceRackId = 4;

app.param('spiceRackId', (req, res, next, id) => {
  const idToFind = Number(id);
  const rackIndex = spiceRacks.findIndex(spiceRack => spiceRack.id === idToFind);
  if (rackIndex !== -1) {
    req.spiceRack = spiceRacks[rackIndex];
    req.spiceRackIndex = rackIndex;
    next();
  } else {
    res.status(404).send('Spice Rack Not Found.');
  }
});

app.get('/spice-racks/', (req, res, next) => {
 res.send(spiceRacks);
});

app.post('/spice-racks/', (req, res, next) => {
  const newRack = req.body.spiceRack;
  newRack.id = nextSpiceRackId++;
  spiceRacks.push(newRack);
  res.send(newRack);
});

app.get('/spice-racks/:spiceRackId', (req, res, next) => {
  res.send(req.spiceRack);
});

app.put('/spice-racks/:spiceRackId', (req, res, next) => {
  const updatedRack = req.body.spiceRack;
  if (req.spiceRack.id !== updatedRack.id) {
    res.status(400).send('Cannot update Spice Rack Id');
  } else {
    spiceRacks[req.spiceRackIndex] = updatedRack;
    res.send(spiceRacks[req.spiceRackIndex]);
  }
});

app.delete('/spice-racks/:spiceRackId', (req, res, next) => {
  spiceRacks.splice(req.spiceRackIndex, 1);
  res.status(204).send();
});

const spicesRouter = require('./spicesRouter');

// Write your code below:
app.use('/spice-racks/:spiceRackId/spices', spicesRouter);

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```
## Key Points
- The router is mounted using app.use('/spice-racks/:spiceRackId/spices', spicesRouter)

- The spicesRouter needs to be configured with {mergeParams: true}

- New spices should be associated with their rack via newSpice.spiceRackId = Number(req.params.spiceRackId)

# Review  
**7 min**  

`router.param` is a powerful tool that we can use to keep our code from repeating core functionality through routes. This is a pattern we want to frequently follow: identify multiple pieces of code that accomplish the same goal, put it into a single component, let that component do that thing (and update it when we want the thing it does to change — in a single place).  

Let's try applying that knowledge again, to another codebase. If you look at the workspace you'll find the same problem of data-lookup happening, based on a URL parameter, multiple times in different places. Try combining that logic in a single place using `router.param`.  

## Refactoring Steps  

1. Refactor the current application to use an `app.param` to handle all routes with `snackId`. It should set the `req.snackIndex` if it exists and send the proper 404 response if not. Make sure to fix all routes to use the `req.snackIndex` and remove duplicate code.  

## Refactored Code  

```javascript
const express = require('express');
const app = express();
const bodyParser = require('body-parser');

app.use(express.static('public'));

const PORT = process.env.PORT || 4001;

const vendingMachine = [
  {
    id: 1,
    name: 'Gum',
    price: 1.25,
  },
  {
    id: 7,
    name: 'Bag of chips',
    price: 3.50,
  },
  {
    id: 23,
    name: 'cumin',
    price: .75,
  }
];

let nextSnackId = 24;

app.use(bodyParser.json());

// Add your code here:
app.param('snackId', (req, res, next, id) => {
  let snackId = Number(id);
  const snackIndex = vendingMachine.findIndex(snack => snack.id === snackId);
  if (snackIndex === -1) {
    res.status(404).send('Snack not found!');
  } else {
    req.snackIndex = snackIndex;
    next();
  }
})

app.get('/snacks/', (req, res, next) => {
  res.send(vendingMachine);
});

app.post('/snacks/', (req, res, next) => {
  const newSnack = req.body;
  if (!newSnack.name || !newSnack.price) {
    res.status(400).send('Snack not found!');
  } else {
    newSnack.id = nextSnackId++;
    vendingMachine.push(newSnack);
    res.send(newSnack);
  }
});

app.get('/snacks/:snackId', (req, res, next) => {
  res.send(vendingMachine[req.snackIndex]);
});

app.put('/snacks/:snackId', (req, res, next) => {
  vendingMachine[req.snackIndex] = req.body;
  res.send(vendingMachine[req.snackIndex]);
});

app.delete('/snacks/:snackId', (req, res, next) => {
  vendingMachine.splice(req.snackIndex, 1);
  res.status(204).send();
});

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

# Off-Platform Project: Boss Machine

## Project Overview
In this project, you will create an entire API to serve information to a Boss Machine, a unique management application for today's most accomplished (evil) entrepreneurs. You will create routes to manage your 'minions', your brilliant 'million dollar ideas', and to handle all the annoying meetings that keep getting added to your busy schedule.

You can view a video demonstration of the final app here:

## How to Begin
To start, download the starting code for this project here. After downloading the zip folder, double click it to uncompress it and access the contents.

Once you have the project downloaded, you'll need to run some terminal commands to get the application started. First, open the root project directory in your terminal. Run `npm install` to install the dependencies of this project and build the front-end application. Once it has finished installing, you can run `npm run start` to begin your server. You'll see `Server listening on port 4001` in the terminal. The `npm run start` script will automatically restart your server whenever you make changes to the `server.js` file or `server/` folder. If you want to turn this off, simply start your server with the `node server.js` command. You can kill either process with the `Ctrl + C` command.

To see the application in its initial, non-working state, simply open `index.html` in a web browser. You should use Google Chrome (at least version 60) or Firefox (at least version 55). The links above will let you download the latest release of either browser if you do not have it or are unsure of which version you're running.

## Implementation Details
To complete the project, you will need to complete code in a few sections of the project. Generally, you will not have to touch anything inside the `browser`, `public`, or `node_modules` folders unless you know some React and HTML/CSS and want to customize the look of the Boss Machine. Before doing any of that, however, let's focus on getting the API server up and running:

### Server Boilerplate
In `server.js`, you will see some boilerplate code, but the server is missing key functionality to allow it to run. You must:
- Set up body-parsing middleware with the `body-parser` package.
- Set up CORS middleware with the `cors` package. You can use the default settings.
- Mount the existing `apiRouter` at `/api`. This router will serve as the starting point for all your API routes.
- Start the server listening on the provided `PORT`. Make sure to use the `PORT` constant and not a hard-coded number, as this is required for tests to run.

Take note of the comments in `server.js`, as your code needs to fit into specific places around the existing boilerplate.

### API Routes
- Your routes should live inside the `server` folder. The file and router structure is up to you, the testing suite will only test whether your API endpoints work as intended, not how you nest your code!
- Your 'database' exists in `server/db.js`. The beginning database will be seeded every time the server is restarted. There is more information on working with the database and the helper functions it exports below.

### Routes Required
#### `/api/minions`
- `GET /api/minions` to get an array of all minions.
- `POST /api/minions` to create a new minion and save it to the database.
- `GET /api/minions/:minionId` to get a single minion by id.
- `PUT /api/minions/:minionId` to update a single minion by id.
- `DELETE /api/minions/:minionId` to delete a single minion by id.

#### `/api/ideas`
- `GET /api/ideas` to get an array of all ideas.
- `POST /api/ideas` to create a new idea and save it to the database.
- `GET /api/ideas/:ideaId` to get a single idea by id.
- `PUT /api/ideas/:ideaId` to update a single idea by id.
- `DELETE /api/ideas/:ideaId` to delete a single idea by id.

#### `/api/meetings`
- `GET /api/meetings` to get an array of all meetings.
- `POST /api/meetings` to create a new meeting and save it to the database.
- `DELETE /api/meetings` to delete all meetings from the database.

For all `/api/minions` and `/api/ideas` routes, any POST or PUT requests will send their new/updated resources in the request body. POST request bodies will not have an `id` property, you will have to set it based on the next id in sequence.

For `/api/meetings POST` route, no request body is necessary, as meetings are generated automatically by the server upon request. Use the provided `createMeeting` function exported from `db.js` to create a new meeting object.

### Working with the 'Database'
The `server/db.js` file exports helper functions for working with the database arrays. The goal of this project is for you to focus on Express routes and not worry about how the database works under the hood. These functions always take at least one argument, and the first argument is always a string representing the name of the database model: `'minions'`, `'ideas'`, `'meetings'`, or `'work'`.

#### `getAllFromDatabase`:
- Takes only the single argument for model name. Returns the array of elements in the database or `null` if an invalid argument is supplied

#### `getFromDatabaseById`:
- Takes the model name argument and a second string argument representing the unique ID of the element. Returns the instance with valid inputs and `null` with an invalid id.

#### `addToDatabase`:
- Takes the model name argument and a second argument which is an object with the key-value pairs of the new instance. `addToDatabase` handles assigning `.id` properties to the instances. It does not check to make sure that valid inputs are supplied, so you will have to add those checks to your routes if necessary. `addToDatabase` will return the newly-created instance from the database. This function will validate the schema of the instance to create and throw an error if it is invalid.

#### `updateInstanceInDatabase`:
- Takes the model name argument and a second argument which is an object representing an updated instance. The instance provided must have a valid `.id` property which will be used to match. `updateInstanceInDatabase` will return the updated instance in the database or `null` with invalid inputs. This function will validate the schema of the updated instance and throw an error if it is invalid.

#### `deleteFromDatabasebyId`:
- Takes the model name argument and a second string argument representing the unique ID of the element to delete. Returns `true` if the delete occurs properly and `false` if the element is not found.

#### `deleteAllFromDatabase`:
- Takes only the single argument for model name. Deletes all elements from the proper model and returns a new, empty array. You will only need to use this function for a `/api/meetings` route.

### Schemas
#### Minion:
- `id`: string
- `name`: string
- `title`: string
- `salary`: number

#### Idea
- `id`: string
- `name`: string
- `description`: string
- `numWeeks`: number
- `weeklyRevenue`: number

#### Meeting
- `time`: string
- `date`: JS Date object
- `day`: string
- `note`: string

Take note that many values that could be numbers are in fact strings. Since we are writing an API, we can't trust that data is always provided by a client. You may need to transform between String and Number JavaScript types in order to provide full functionality in your API.

### Custom Middleware
- You will create a custom middleware function `checkMillionDollarIdea` that will come in handy in some `/api/ideas` routes. Write this function in the `server/checkMillionDollarIdea.js` file. This function will make sure that any new or updated ideas are still worth at least one million dollars! The total value of an idea is the product of its `numWeeks` and `weeklyRevenue` properties.

## Bonus
As a bonus, you may implement routes to allow bosses to add and remove work from their minions' backlogs.

### Schema:
#### Work:
- `id`: string
- `title`: string
- `description`: string
- `hours`: number
- `minionId`: string

### Routes required:
- `GET /api/minions/:minionId/work` to get an array of all work for the specified minion.
- `POST /api/minions/:minionId/work` to create a new work object and save it to the database.
- `PUT /api/minions/:minionId/work/:workId` to update a single work by id.
- `DELETE /api/minions/:minionId/work/:workId` to delete a single work by id.

To work on the bonus with tests, you will need to remove their pending status. Open the `test/test.js` and edit that begins the `/api/minions/:minionId/work` routes tests. It should start with `xdescribe(` around line 689 of the test file. If you delete the `x` (so that the line simply starts with `describe(` and save the test file before re-running, your bonus tests will now be active.

In order to fully implement these routes, the database helper functions may not provide all the functionality that you need, and you may need to use router parameters or other methods to attach the `minionId` properties correctly and handle the edge cases property. Good luck!

## Testing
A testing suite has been provided for you, checking for all essential functionality and edge cases.

To run these tests, first open the root project directory in your terminal. Then run `npm install` to install all necessary testing dependencies (you will only need to do this step once).

Finally, run `npm run test`. You will see a list of tests that ran with information about whether or not each test passed. After this list, you will see more specific output about why each failing test failed. While they are open in a terminal window, these tests will re-run every time you save server files. If you want to quit the testing loop, use `Ctrl + C`. If you only want to run the tests once, you can run the `mocha` command in the terminal from your project root directory.

As you implement functionality, run the tests to ensure you are implementing your routes and middleware correctly. The tests will additionally help you identify edge cases that you may not have anticipated when first writing your routes. You should also test the functionality on the frontend to make sure that things are working as intended. Feel free to add logging middleware to your server, it will help with debugging!


## Review: Build a Back-End with Express.js
Review what you just learned in the Build a Back-End with Express.js Unit.

Congratulations! The goal of this unit was to learn about the popular back-end environment, Node.js, and how to create back-end servers and APIs in JavaScript using the popular Express.js framework. With this knowledge, you have the foundation for creating compelling, dynamic web servers. In the next unit, you will learn how to write tests for your back-end server.

### Key Learning Outcomes
Having completed this unit, you are now able to:
- Understand Node.js
- Create a server with Express
- Design/serve RESTful APIs
- Understand what CORS is
- Explain routing

### Additional Resources
If you are interested in learning more about these topics, here are some additional resources:
- **Reading**: [Eloquent Javascript Chapter 20: Node.js](https://eloquentjavascript.net/20_node.html), Marijn Haverbeke
- **Tutorial**: [Express web framework (Node.js/JavaScript)](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs), MDN
- **Article**: [Going out to eat and understanding the basics of Express.js](https://blog.codeanalogies.com/2016/04/11/going-out-to-eat-and-understanding-the-basics-of-express-js/), Kevin Kononenko
- **Resource**: [Express.js: Express Middleware Modules](https://expressjs.com/en/resources/middleware.html)

### Portfolio Project Preparation
Remember, you will put all of this knowledge into practice with an upcoming Portfolio Project. If you ever get stuck while working on the project, you can come back to this Unit and review what you have learned.

### Community Engagement
Learning is social. Whatever you're working on, be sure to connect with the Codecademy community in the forums. Remember to check in with the community regularly, including for things like:
- Code review on your project work
- Guidance on materials needed to accomplish your goals
- Troubleshooting help
- Sharing your progress and learning from others
















