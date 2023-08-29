# Mongoose

[Mongoose Docs](https://mongoosejs.com/docs/)

## What is Mongoose?

Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js. It manages relationships between data, provides schema validation, and is used to translate between objects in code and the representation of those objects in MongoDB.

MongoDB is a schema-less NoSQL document database. It means you can store JSON documents in it, and the structure of these documents can vary as it is not enforced like SQL databases. This is one of the advantages of using NoSQL as it speeds up application development and reduces the complexity of deployments.

[Introduction to Mongoose](https://www.freecodecamp.org/news/introduction-to-mongoose-for-mongodb-d2a7aa593c57/)

## Terminologies

- Collections: Collections in Mongo are equivalent to tables in relational databases. They can hold multiple JSON documents.
- Documents: Documents are equivalent to records or rows of data in SQL. While a SQL row can reference data in other tables, Mongo documents usually combine that in a document.
- Fields: Fields, also known as properties or attributes, are similar to columns in a SQL table.
- Schema: While Mongo is schema-less, SQL defines a schema via the table definition. A Mongoose schema is a document data structure (or shape of the document) that is enforced via the application layer.
- SchemaTypes: While Mongoose schemas define the overall structure or shape of a document, SchemaTypes define the expected data type for individual fields (String, Number, Boolean, and so on). You can also pass in useful options like required to make a field non-optional, default to set a default value for the field, and many more.
    - Permitted SchemaTypes include: String, Number, Date, Buffer, Boolean, Mixed, ObjectId, Array, Decimal128, Map, UUID
- Models: Models are higher-order constructors that take a schema and create an instance of a document equivalent to records in a relational database.

- puppySchema defines the shape of the document
- the schemaType for name is String, can use an object to add additional properties like required
- Puppy is the Schema compiled into a Model to be used later on to construct documents in an application
~~~
const puppySchema = new mongoose.Schema({
  name: {
    type: String,
    required: true
  },
  age: Number
});

const Puppy = mongoose.model('Puppy', puppySchema);
~~~

## Installation

~~~
npm init
npm install mongoose
~~~

## Create a Mongoose Model
1. Reference Mongoose
~~~
let mongoose = require('mongoose');
~~~
2. Define the Schema
~~~
let emailSchema = new mongoose.Schema({
  email: String
});
~~~
3. Export Model
~~~
module.exports = mongoose.model('Email', emailSchema);
~~~



## Schemas 
[Schemas](https://mongoosejs.com/docs/guide.html)

### Define your Schema
Everything in Mongoose starts with a Schema. Each schema maps to a MongoDB collection and defines the shape of the documents within that collection.

~~~
import mongoose from 'mongoose';
const { Schema } = mongoose;

const blogSchema = new Schema({
  title: String, // String is shorthand for {type: String}
  author: String,
  body: String,
  comments: [{ body: String, date: Date }],
  date: { type: Date, default: Date.now },
  hidden: Boolean,
  meta: {
    votes: Number,
    favs: Number
  }
});
~~~

### Create a Model

To use our schema definition, we need to convert our blogSchema into a Model we can work with. To do so, we pass it into mongoose.model(modelName, schema):

~~~
const Blog = mongoose.model('Blog', blogSchema);
~~~

### Ids

By default, Mongoose adds an _id property to your schemas.

You can also overwrite Mongoose's default _id with your own _id. Just be careful: Mongoose will refuse to save a document that doesn't have an _id, so you're responsible for setting _id if you define your own _id path.

### Instance Methods

Instances of Models are documents. Documents have many of their own built-in instance methods. We may also define our own custom document instance methods.


## SchemaTypes
[SchemaTypes](https://mongoosejs.com/docs/schematypes.html)

## Connections
[Connections](https://mongoosejs.com/docs/connections.html)

## Models
[Models](https://mongoosejs.com/docs/models.html)

## Queries
[Queries](https://mongoosejs.com/docs/queries.html)

## Validation
[Validation](https://mongoosejs.com/docs/validation.html)

## Middleware
[Middleware](https://mongoosejs.com/docs/middleware.html)

## Typescript Support
[Typescript Support](https://mongoosejs.com/docs/typescript.html)