Serverless MongoDB Rest API with Mongoose and Bluebird Promises

This example demonstrate how to use a MongoDB database with aws and serverless.

Using Mongoose ODM and Bluebird for Promises.

Use Cases

NoSQL CRUD API
Setup

npm install
serverless deploy


#endpoints:
  -POST - https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user
  -PUT - https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/{id}
  -DELETE - https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/{id}
  -GET - https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/{id}
#functions:
  -createUser: aws-node-rest-api-mongodb-dev-createUser
  -updateUser: aws-node-rest-api-mongodb-dev-updateUser
  -deleteUser: aws-node-rest-api-mongodb-dev-deleteUser
  -user: aws-node-rest-api-mongodb-dev-user


Usage

In handler.js update the mongoString with your mongoDB url.

Create

curl -XPOST -H "Content-type: application/json" -d '{
   "name" : "John",
   "firstname" : "Doe",
   "city" : "Toronto",
   "birth" : "01/01/1990"
}' 'https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/'
{"id": "590b52ff086041000142cedd"}
READ

curl -XGET -H "Content-type: application/json" 'https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/590b52ff086041000142cedd'
[
  {
    "_id": "5905e2fbdb55f20001334b3e",
    "name": "John",
    "firstname": "Doe",
    "birth": null,
    "city": "Toronto",
    "ip": "01/01/1990",
    "__v": 0
  }
]
UPDATE

curl -XPUT -H "Content-type: application/json" -d '{
   "name" : "William",
   "firstname" : "Smith",
   "city" : "Miami",
   "birth" : "01/01/2000"
}' 'https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/590b52ff086041000142cedd'
"Ok"
DELETE

curl -XDELETE -H "Content-type: application/json" 'https://xxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/user/590b52ff086041000142cedd'
"Ok"
