# Introduction-to-MongoDB

## Q-1 What is MongoDB ?

MongoDB is a popular NoSQL database that stores data in a flexible, JSON-like format called BSON (Binary JSON). Unlike traditional relational databases, MongoDB is schema-less, meaning it doesn't require a fixed structure for data, allowing for easier scalability and faster development. It's widely used for handling large volumes of unstructured data and is known for its performance, flexibility, and scalability in handling modern web applications.

## Q-2 How to use MongoDB and Why we use it ?

**How to use MongoDB:**

1. **Install MongoDB**: Download and install MongoDB from its official website or use a cloud service like MongoDB Atlas.

2. **Start MongoDB**: Run the MongoDB server using the `mongod` command.

3. **Connect to MongoDB**: Use the MongoDB shell (`mongo`) or a driver/library in your application (like Mongoose for Node.js) to connect to the database.

4. **Create a Database and Collections**: Use commands or drivers to create a database and collections (equivalent to tables in SQL).

5. **Insert Data**: Add documents (records) to your collections using commands or methods.

6. **Query Data**: Retrieve and manipulate data with various query methods.

7. **Update and Delete Data**: Use update and delete operations to modify or remove documents.

**Why use MongoDB:**

- **Flexible Schema**: Allows for a dynamic schema, making it easy to adjust to changing data requirements.
- **Scalability**: Handles large volumes of data and scales horizontally by adding more servers.
- **Performance**: Optimized for read and write performance with features like indexing.
- **Ease of Use**: JSON-like format is intuitive and easy to work with, especially in modern web applications.
- **Rich Query Language**: Supports complex queries and aggregations, making it versatile for various use cases.

## Simple MongoDB Example ##
```javascript
db.students.insertMany([
  { id: 1, name: 'Ryan', gender: 'M' },
  { id: 2, name: 'Joanna', gender: 'F' },
  { id: 3, name: 'Jhon', gender: 'M' },
  { id: 4, name: 'Alex', gender: 'M' },
  { id: 5, name: 'Bru', gender: 'F' },
  { id: 6, name: 'Jack', gender: 'M'},
  { id: 7, name: 'Thomas', gender: 'M' },
  { id: 8, name: 'Noah', gender: 'F' },
  { id: 9, name: 'Leo', gender: 'M' },
  { id: 10, name: 'Harry', gender: 'M' },
  { id: 11, name: 'Oliver', gender: 'F' },
  { id: 12, name: 'William', gender: 'F' },
  { id: 13, name: 'Adam', gender: 'M' },
  { id: 14, name: 'Sophia', gender: 'F' }
    
]);
db.students.find({ gender: 'F' });

db.students.find({ gender: 'M' });


```

## Q-3 What are the benefits of it ?

MongoDB offers several benefits:

1. **Flexible Schema**: Allows you to store documents with varying structures, which is useful for applications where data models are constantly evolving.

2. **Scalability**: Easily scales horizontally by sharding data across multiple servers, which helps manage large amounts of data and high traffic loads.

3. **High Performance**: Optimized for high read and write performance with features like in-memory processing and indexing.

4. **Rich Query Capabilities**: Supports a wide range of queries and aggregations, enabling complex data retrieval and manipulation.

5. **Developer Productivity**: Its JSON-like document model maps directly to application objects, simplifying development and reducing the need for complex mapping.

6. **Replication and High Availability**: Provides automatic replication and failover through replica sets, enhancing data durability and availability.

7. **Ease of Integration**: Works well with modern technologies and frameworks, and has a variety of official drivers and community-supported libraries for different programming languages.

 ## Q-4 What is MongoDB used for ?

MongoDB is used for various purposes due to its flexible and scalable nature. Common use cases include:

1. **Content Management Systems**: Ideal for managing and delivering dynamic content, such as articles, blogs, and media.

2. **Real-Time Analytics**: Handles high volumes of data and provides real-time insights, often used in dashboards and data visualization tools.

3. **Internet of Things (IoT)**: Stores and processes data from IoT devices, which can be voluminous and vary in structure.

4. **Mobile and Web Applications**: Powers modern applications by managing user data, session data, and application state.

5. **E-Commerce**: Manages product catalogs, customer information, and order histories, allowing for flexible data modeling and scaling.

6. **Social Networks**: Supports user profiles, social interactions, and real-time data feeds.

7. **Gaming**: Manages game data, user profiles, and in-game transactions with high performance and scalability.

8. **Geospatial Data**: Handles location-based data and queries, such as mapping and location-based services.


## Q-5 What are the advantages of mongoDB ?

MongoDB offers several advantages:

1. **Flexible Schema**: Unlike traditional relational databases, MongoDB allows for a flexible schema design, meaning you can store different types of data in the same collection without needing to define a fixed schema upfront.

2. **Scalability**: It supports horizontal scaling through sharding, which means you can distribute data across multiple servers as your application grows.

3. **High Performance**: MongoDB provides high performance for read and write operations due to its in-memory processing and efficient indexing.

4. **Document-Oriented**: It stores data in BSON (binary JSON) format, making it easier to represent complex hierarchical data and nested objects.

5. **Real-Time Data Processing**: It supports real-time data processing and aggregation, which is useful for applications that require fast analytics and reporting.

6. **Ease of Use**: MongoDB’s query language is intuitive and its integration with various programming languages and frameworks is straightforward.

## Q-6 What is the main feature of MongoDB ?

The main feature of MongoDB is its **document-oriented storage model**. It stores data in JSON-like documents (BSON format), which allows for a flexible and dynamic schema. This means you can have different fields and data types within the same collection, making it easier to handle diverse and evolving data structures.

## Q-7 What is MongoDB Query API ?

MongoDB Query API is a set of functions and methods provided by MongoDB to interact with your MongoDB database. It allows you to perform operations like querying, inserting, updating, and deleting documents in a MongoDB database.

Here’s a brief overview of some key features:

1. **Querying Documents**: You can search for documents in a collection using various query operators and expressions. For example, you can use `{ "name": "Alice" }` to find documents where the `name` field is "Alice".

2. **Projection**: Specify which fields you want to include or exclude in the result. For example, `{ "name": 1, "age": 1 }` will include only the `name` and `age` fields in the result.

3. **Sorting**: You can sort the results of a query using the `.sort()` method. For example, `.sort({ "age": -1 })` will sort documents by `age` in descending order.

4. **Pagination**: Methods like `.limit()` and `.skip()` help manage large result sets by limiting the number of results returned or skipping a certain number of documents.

5. **Aggregation**: For more complex queries, MongoDB provides an aggregation framework that allows you to perform operations like filtering, grouping, and transforming data.

6. **Update Operations**: You can update documents using methods like `.updateOne()`, `.updateMany()`, or `.replaceOne()`.

7. **Deletion**: Remove documents with methods like `.deleteOne()` or `.deleteMany()`.

```javascript
const MongoClient = require('mongodb').MongoClient;
const url = 'mongodb://localhost:27017';
const dbName = 'mydatabase';

MongoClient.connect(url, { useNewUrlParser: true, useUnifiedTopology: true }, (err, client) => {
  if (err) throw err;

  const db = client.db(dbName);
  const collection = db.collection('mycollection');

  // Querying documents
  collection.find({ "name": "Alice" }).toArray((err, docs) => {
    if (err) throw err;

    console.log(docs);
    client.close();
  });
});
```

## Q-8How to handle dynamic response in mongoDB ?

Handling dynamic responses in MongoDB involves managing data that may vary in structure or content. MongoDB's flexible schema allows you to store documents with different fields in the same collection, which makes it ideal for dynamic data. Here's how you can handle dynamic responses conceptually:

### 1. **Schema Flexibility**
   - MongoDB is a NoSQL database, so it doesn't require a predefined schema. This allows you to store documents with varying structures within the same collection. For example, you can have documents with different fields or types of data depending on the response you need to store.

### 2. **Storing Dynamic Data**
   - When you receive dynamic data (e.g., varying API responses, user-generated content), you can store it as-is in MongoDB. Each document can have a different structure, and MongoDB will store it without any issues. This flexibility is one of the key advantages of MongoDB.

### 3. **Querying Dynamic Data**
   - MongoDB allows you to query documents even if they have different structures. You can query specific fields that may or may not exist in all documents. For instance, you can search for documents that contain a particular field or match a certain structure.

### 4. **Indexing Dynamic Fields**
   - Although MongoDB allows for flexible schemas, you can still create indexes on fields that you frequently query, even if those fields are not present in every document. This can improve query performance on dynamic data.

### 5. **Handling Missing or Extra Fields**
   - Since MongoDB documents don't have to conform to a strict schema, you can handle cases where fields might be missing or where extra fields are present. When querying, you can account for this variability by checking if fields exist or by handling null values appropriately.

### 6. **Data Normalization and Embedding**
   - Depending on your use case, you might choose to normalize your data (i.e., store related information in separate documents) or embed related data within the same document. MongoDB supports both approaches, allowing you to model your data dynamically based on your application's needs.

### 7. **Dynamic Data Processing**
   - When working with dynamic responses, it's important to process and validate the data before storing it in MongoDB. This ensures that the data is in a consistent state and that any necessary transformations (like data type conversions) are handled appropriately.


## Q-9 Introduction of Async, Await try and catch Async, Await in mongoDB ?

In MongoDB, when interacting with databases, especially in Node.js, operations like querying, inserting, updating, or deleting data are often asynchronous. This means they don't execute instantly and can take time to complete, especially if the database is large or the network is slow.

### **Async/Await**
- **Async**: The `async` keyword is used to define an asynchronous function. Inside this function, you can write code that performs asynchronous operations in a more readable and linear manner, similar to synchronous code.
  
- **Await**: The `await` keyword is used to pause the execution of the code within an `async` function until a Promise (usually returned by an asynchronous operation like a MongoDB query) is resolved or rejected. This makes the code appear synchronous, allowing for easier reading and debugging.

### **Try/Catch with Async/Await**
- **Try/Catch**: In an `async` function, you can use `try/catch` blocks to handle errors that might occur during the execution of asynchronous operations. This is particularly useful with MongoDB operations, where network issues, query errors, or connection problems could arise.
  
Using `try/catch`, you can catch these errors and handle them appropriately, whether by logging the error, retrying the operation, or sending a response back to the client in a web application.


## Q-10 Setting up Directory Structure of Express MVC Setup Express Routers ?

Setting up a directory structure for an Express application using the MVC (Model-View-Controller) pattern involves organizing your code into separate folders for models, views, and controllers, along with other supporting directories like routes, config, and public. Here's how you can set it up:

### 1. Directory Structure

A typical Express MVC directory structure might look like this:

```
my-express-app/
├── config/
│   └── config.js
├── controllers/
│   └── userController.js
├── models/
│   └── userModel.js
├── routes/
│   └── userRoutes.js
├── views/
│   ├── layout.ejs
│   └── user.ejs
├── public/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── script.js
├── node_modules/
├── app.js
├── package.json
└── .env
```

### 2. Explanation of Each Directory and File

- **config/**: Contains configuration files, like database connection settings.
- **controllers/**: Contains the logic that interacts with the models and prepares data to be sent to the views.
- **models/**: Represents the data structure (e.g., using Mongoose for MongoDB).
- **routes/**: Contains route definitions, which map URLs to specific controller actions.
- **views/**: Contains the templates for the user interface, often using a templating engine like EJS, Pug, or Handlebars.
- **public/**: Contains static files like CSS, JavaScript, images, etc.
- **app.js**: The main entry point for the application. It sets up middleware, routes, and starts the server.
- **package.json**: Contains project metadata, dependencies, and scripts.
- **.env**: Stores environment variables like database URIs or API keys.

### 3. Setting Up Express Routers

Let's set up a basic Express Router for a user management system.

**app.js**:
```javascript
const express = require('express');
const app = express();
const userRoutes = require('./routes/userRoutes');

// Middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Routes
app.use('/users', userRoutes);

// Start the server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
});
```

**routes/userRoutes.js**:
```javascript
const express = require('express');
const router = express.Router();
const userController = require('../controllers/userController');

// Define routes and map them to controller methods
router.get('/', userController.getAllUsers);
router.post('/', userController.createUser);
router.get('/:id', userController.getUserById);
router.put('/:id', userController.updateUser);
router.delete('/:id', userController.deleteUser);

module.exports = router;
```

**controllers/userController.js**:
```javascript
const User = require('../models/userModel');

exports.getAllUsers = (req, res) => {
    // Logic to get all users
    res.send('Get all users');
};

exports.createUser = (req, res) => {
    // Logic to create a new user
    res.send('Create a user');
};

exports.getUserById = (req, res) => {
    const { id } = req.params;
    // Logic to get a user by ID
    res.send(`Get user with ID ${id}`);
};

exports.updateUser = (req, res) => {
    const { id } = req.params;
    // Logic to update a user by ID
    res.send(`Update user with ID ${id}`);
};

exports.deleteUser = (req, res) => {
    const { id } = req.params;
    // Logic to delete a user by ID
    res.send(`Delete user with ID ${id}`);
};
```

**models/userModel.js**:
```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
    name: String,
    email: String,
    password: String,
});

const User = mongoose.model('User', userSchema);

module.exports = User;
```

### 4. Running the Project

1. **Install Dependencies**:
   ```bash
   npm install express mongoose dotenv
   ```

2. **Start the Server**:
   ```bash
   node app.js
   ```

This setup provides a basic structure to start building your Express application using the MVC pattern.

## Q-11 Middleware concept in MVC make static files assests attach internal and external filels ?

### Middleware Concept in MVC:
- **Middleware** acts as a bridge between the request and the response in an application. It processes incoming requests before they reach the controller and can also handle responses before they are sent back to the client.
- Middleware functions can be used for various purposes, such as authentication, logging, error handling, and modifying request/response objects.

### Handling Static Files:
- **Static Files** (like CSS, JavaScript, images) are assets that do not change during runtime. Middleware can serve these static files directly to the client.
- When a request is made for a static file, the middleware intercepts it, retrieves the file from the specified directory, and sends it to the client without involving the controller.

### Internal and External Files:
- **Internal Files**: These are static assets or resources stored within the application's directory structure (e.g., in a `public` or `assets` folder).
- **External Files**: These could be files hosted on external servers or CDNs. Middleware can be configured to fetch these files and serve them to the client.

## Q-12 What is the difference between MongoDB and MySQL ?

MongoDB and MySQL are both popular databases but differ significantly in their structure and use cases:

1. **Data Model**:
   - **MongoDB**: A NoSQL database that stores data in a flexible, JSON-like format called BSON (Binary JSON). It is schema-less, meaning you can store documents with different structures in the same collection.
   - **MySQL**: A relational database that stores data in tables with a fixed schema. Data is organized into rows and columns, and relationships are defined using foreign keys.

2. **Scalability**:
   - **MongoDB**: Designed for horizontal scalability, making it easier to distribute data across multiple servers.
   - **MySQL**: Typically scaled vertically (by adding more resources to a single server), though it can be scaled horizontally with more effort.

3. **Query Language**:
   - **MongoDB**: Uses its own query language, which allows for complex queries using a more flexible, document-oriented approach.
   - **MySQL**: Uses SQL (Structured Query Language), a standard language for managing relational databases.

4. **Use Cases**:
   - **MongoDB**: Ideal for applications that require flexible, evolving data structures, such as real-time analytics, content management, and IoT.
   - **MySQL**: Best suited for applications that require complex transactions and data integrity, such as e-commerce platforms, financial systems, and legacy applications.
  
## Q-13 What is SQL and NoSQL in MongoDB ?

SQL and NoSQL are two types of database management systems, each with its own approach to handling and storing data. Here's a brief overview of both:

### SQL (Structured Query Language)

- **Relational Database**: SQL databases are relational, meaning they store data in structured tables with rows and columns. They use schemas to define the structure of data and relationships between tables.
- **Examples**: MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server.
- **Query Language**: SQL databases use Structured Query Language (SQL) for querying and managing data.
- **ACID Compliance**: SQL databases are typically ACID-compliant, ensuring transactions are processed reliably.

### NoSQL (Not Only SQL)

- **Non-relational Database**: NoSQL databases are non-relational and can store data in various formats such as documents, key-value pairs, wide-columns, or graphs.
- **Examples**: MongoDB, Cassandra, Redis, Couchbase.
- **Flexible Schema**: NoSQL databases often have a more flexible schema or schema-less design, allowing for more dynamic and scalable data structures.
- **MongoDB**: MongoDB is a popular NoSQL database that stores data in a flexible, JSON-like format called BSON (Binary JSON). It is designed to handle large volumes of unstructured or semi-structured data and provides scalability and high performance.

### MongoDB Specifics

- **Document-Oriented**: MongoDB stores data in collections of JSON-like documents. Each document can have a different structure, making it easy to store and query diverse types of data.
- **Query Language**: MongoDB uses a query language that is similar to JSON syntax for querying and manipulating data.
- **Scalability**: MongoDB is designed to scale horizontally, making it suitable for handling large amounts of data and high-throughput applications.

## Q-14 What is DBMS in MongoDB ?

DBMS stands for Database Management System, which is software designed to manage, store, and retrieve data in a database. MongoDB is a type of NoSQL DBMS, and it handles data differently compared to traditional relational databases.

### MongoDB as a DBMS

1. **Document-Oriented**: MongoDB is a document-oriented database, which means it stores data in JSON-like documents (using BSON format) rather than in tables with rows and columns. Each document can have a unique structure, allowing for flexibility in how data is stored and queried.

2. **Schema Flexibility**: Unlike relational databases, MongoDB does not require a fixed schema. This means you can have documents with varying structures within the same collection, making it adaptable to changes and new data types.

3. **Scalability**: MongoDB is designed to scale horizontally, which means it can handle large volumes of data and high traffic by distributing the load across multiple servers.

4. **High Performance**: MongoDB provides high performance for read and write operations through features like indexing, in-memory processing, and optimized query execution.

5. **Rich Query Language**: MongoDB uses a powerful query language that supports a wide range of operations, including searching, filtering, and aggregation, all using a syntax similar to JSON.

6. **Replication and Sharding**: MongoDB supports data replication through replica sets, which ensure data redundancy and high availability. It also supports sharding, a method of distributing data across multiple servers to balance the load and enhance performance.

7. **Integration and Tools**: MongoDB provides various tools and integrations for data management, including MongoDB Atlas (a cloud-based managed service), Compass (a graphical user interface), and drivers for different programming languages.

## Q-15 Queries and Params in MongoDB ?

In MongoDB, queries and parameters are used to retrieve and manipulate data stored in the database. Here's a breakdown of how they work:

### Queries in MongoDB

MongoDB queries are used to search for and retrieve documents from a collection. The query language is designed to be similar to JSON, making it intuitive for developers familiar with JSON data.

#### Basic Query Syntax

- **Find Documents**: To retrieve documents from a collection, you use the `find()` method. For example:
  ```javascript
  db.collection.find({ key: value });
  ```
  This query returns all documents where the `key` field matches `value`.

- **Query Operators**: MongoDB supports various query operators for more complex queries:
  - **Comparison Operators**: Such as `$eq` (equals), `$ne` (not equal), `$gt` (greater than), `$lt` (less than), etc.
    ```javascript
    db.collection.find({ age: { $gt: 25 } });
    ```
  - **Logical Operators**: Such as `$and`, `$or`, `$not`, `$nor` to combine multiple conditions.
    ```javascript
    db.collection.find({ $or: [ { age: { $lt: 20 } }, { age: { $gt: 60 } } ] });
    ```
  - **Element Operators**: Such as `$exists` (checks if a field exists) and `$type` (checks the type of a field).
    ```javascript
    db.collection.find({ name: { $exists: true } });
    ```

#### Projection

Projection specifies which fields to include or exclude in the returned documents. For example:
```javascript
db.collection.find({ key: value }, { field1: 1, field2: 1 });
```
This query returns only `field1` and `field2` from the matching documents, while excluding other fields.

### Parameters in MongoDB

Parameters in MongoDB are used to customize queries and operations. Here are some common parameters:

#### `find()` Method Parameters

- **Query Parameter**: The first parameter of `find()` is the query document that specifies the criteria for selecting documents.
- **Projection Parameter**: The second parameter of `find()` specifies which fields to include or exclude.

#### `findOne()` Method

The `findOne()` method retrieves a single document that matches the query criteria:
```javascript
db.collection.findOne({ key: value });
```

#### `update()` and `updateOne()` Methods

- **Update Parameter**: Specifies the update operations to be applied to the matching documents.
  ```javascript
  db.collection.updateOne(
    { key: value }, 
    { $set: { field: newValue } }
  );
  ```

#### `aggregate()` Method

The `aggregate()` method allows for complex data processing and transformations:
```javascript
db.collection.aggregate([
  { $match: { key: value } },
  { $group: { _id: "$field", total: { $sum: "$value" } } }
]);
```

#### `sort()`, `limit()`, and `skip()`

- **Sort**: To sort the results, use the `sort()` method.
  ```javascript
  db.collection.find().sort({ field: 1 }); // 1 for ascending, -1 for descending
  ```

- **Limit**: To limit the number of results, use the `limit()` method.
  ```javascript
  db.collection.find().limit(5);
  ```

- **Skip**: To skip a number of results, use the `skip()` method.
  ```javascript
  db.collection.find().skip(10);
  ```

## Q-16 What is the difference between Mongoose and MongoDB ?

Mongoose and MongoDB serve different purposes in the context of working with MongoDB databases. Here's a breakdown of their differences:

### MongoDB

1. **Database System**: MongoDB is a NoSQL database system that stores data in a flexible, JSON-like format called BSON (Binary JSON). It is used for managing and querying large volumes of unstructured or semi-structured data.

2. **Core Functions**: MongoDB provides the fundamental database functionalities, such as:
   - Storing, retrieving, and manipulating data.
   - Managing data collections and documents.
   - Performing queries and indexing for efficient data access.

3. **Usage**: MongoDB is used directly to interact with your data, handle storage, and manage database operations.

### Mongoose

1. **Object Data Modeling (ODM) Library**: Mongoose is an ODM library for MongoDB and Node.js. It provides a higher-level abstraction for interacting with MongoDB, allowing you to define schemas and models for your data.

2. **Core Features**:
   - **Schema Definition**: Mongoose allows you to define schemas that specify the structure of your data, including validation rules, default values, and data types.
   - **Models**: You can create models based on schemas, which act as constructors for creating and managing documents.
   - **Middleware**: Mongoose supports middleware functions (hooks) that can be used to perform actions before or after certain operations, such as saving or validating documents.
   - **Query Building**: Mongoose provides a more structured and fluent API for building and executing queries compared to the native MongoDB query language.

3. **Usage**: Mongoose is used as an intermediary between your Node.js application and MongoDB. It simplifies the process of working with MongoDB by providing an object-oriented interface and additional features that streamline data management.

### Example Comparison

- **MongoDB Native Query**:
  ```javascript
  db.collection.find({ key: value });
  ```

- **Mongoose Query**:
  ```javascript
  Model.find({ key: value }, function(err, documents) {
    // handle result
  });
  ```

- **Schema Definition with Mongoose**:
  ```javascript
  const mongoose = require('mongoose');
  const Schema = mongoose.Schema;

  const userSchema = new Schema({
    name: String,
    age: Number
  });

  const User = mongoose.model('User', userSchema);
  ```

## Q-17 Consider you are working in amazon one day your manager asked you to build a feature that can actually see the activity of the whole day that at vwhat API endpoint requests has been made along with the timestamp of request then how are you going to implement it ?

To build a feature that tracks API endpoint requests along with their timestamps, we can create a Node.js project using Express.js. Here's a step-by-step guide to implementing this feature:

### Project Setup

1. **Initialize the Project:**
   ```bash
   mkdir api-tracking
   cd api-tracking
   npm init -y
   ```

2. **Install Dependencies:**
   ```bash
   npm install express mongoose dotenv
   npm install --save-dev nodemon
   ```

   - `express`: To create the server and define the endpoints.
   - `mongoose`: To interact with a MongoDB database where we'll store the logs.
   - `dotenv`: To manage environment variables.
   - `nodemon`: For auto-restarting the server during development.

3. **Project Structure:**
   ```
   api-tracking/
   ├── server.js
   ├── .env
   ├── models/
   │   └── RequestLog.js
   ├── routes/
   │   └── api.js
   └── middleware/
       └── logger.js
   ```

### Implementation

#### 1. **Environment Configuration (.env):**

   Create a `.env` file to store environment variables like the MongoDB connection string.

   ```env
   PORT=3000
   MONGO_URI=mongodb://localhost:27017/apiTrackingDB
   ```

#### 2. **Setting Up the Server (server.js):**

   Create the server and connect to MongoDB.

   ```javascript
   const express = require('express');
   const mongoose = require('mongoose');
   const dotenv = require('dotenv');
   const apiRoutes = require('./routes/api');

   dotenv.config();

   const app = express();
   const PORT = process.env.PORT || 3000;

   // MongoDB connection
   mongoose.connect(process.env.MONGO_URI, { useNewUrlParser: true, useUnifiedTopology: true })
     .then(() => console.log('MongoDB connected'))
     .catch(err => console.error(err));

   // Middleware
   app.use(express.json());

   // Routes
   app.use('/api', apiRoutes);

   // Start the server
   app.listen(PORT, () => {
     console.log(`Server running on port ${PORT}`);
   });
   ```

#### 3. **Request Logging Middleware (middleware/logger.js):**

   Create middleware to log each request.

   ```javascript
   const RequestLog = require('../models/RequestLog');

   const logger = async (req, res, next) => {
     const log = new RequestLog({
       method: req.method,
       endpoint: req.originalUrl,
       timestamp: new Date(),
     });

     try {
       await log.save();
       console.log('Request logged:', log);
     } catch (error) {
       console.error('Error logging request:', error);
     }

     next();
   };

   module.exports = logger;
   ```

#### 4. **Request Log Model (models/RequestLog.js):**

   Define a Mongoose schema and model to store the request logs.

   ```javascript
   const mongoose = require('mongoose');

   const requestLogSchema = new mongoose.Schema({
     method: { type: String, required: true },
     endpoint: { type: String, required: true },
     timestamp: { type: Date, required: true },
   });

   const RequestLog = mongoose.model('RequestLog', requestLogSchema);

   module.exports = RequestLog;
   ```

#### 5. **API Routes (routes/api.js):**

   Create some dummy endpoints to demonstrate logging.

   ```javascript
   const express = require('express');
   const router = express.Router();
   const logger = require('../middleware/logger');
   const RequestLog = require('../models/RequestLog');

   // Apply logger middleware to all routes
   router.use(logger);

   // Dummy endpoints
   router.get('/test', (req, res) => {
     res.send('GET request to /test');
   });

   router.post('/test', (req, res) => {
     res.send('POST request to /test');
   });

   // Endpoint to retrieve all logs
   router.get('/logs', async (req, res) => {
     try {
       const logs = await RequestLog.find().sort({ timestamp: -1 });
       res.json(logs);
     } catch (error) {
       res.status(500).json({ message: 'Error retrieving logs', error });
     }
   });

   module.exports = router;
   ```

### Running the Project

1. **Start the Server:**
   ```bash
   nodemon server.js
   ```

2. **Test the API Endpoints:**

   - **GET** `/api/test` - This will trigger a GET request and log it.
   - **POST** `/api/test` - This will trigger a POST request and log it.
   - **GET** `/api/logs` - This will return all logged requests.

### Viewing the Logs

To see all the logged API requests with their timestamps, you can make a GET request to the `/api/logs` endpoint.

### Conclusion

This setup provides a basic implementation of an API request tracking system using Node.js, Express.js, and MongoDB. You can expand on this by adding features such as filtering logs by date, logging response status, etc.


## Explanation

To implement a feature that tracks daily API endpoint requests along with timestamps, you can follow these steps:

1. **Logging Middleware**: Implement a logging middleware that intercepts all incoming API requests. This middleware would log details like the endpoint URL, HTTP method, request payload (if any), and timestamp.

2. **Centralized Logging System**: Store these logs in a centralized logging system such as AWS CloudWatch, Elasticsearch, or any database designed for logging, where each entry includes the endpoint, timestamp, and other relevant metadata.

3. **Data Aggregation**: Use a data aggregation tool or script that can periodically (e.g., hourly or daily) query the log storage to summarize the data, such as the number of requests per endpoint and their timestamps.

4. **Dashboard**: Build a dashboard (using tools like Grafana or Kibana) that visualizes the data. This dashboard should allow you to filter by date, endpoint, and time range to see the activity.

5. **API for Reports**: Optionally, create an API endpoint that can provide a summary report of the logged data for a particular day, showing the count and details of requests made to each endpoint.



  
