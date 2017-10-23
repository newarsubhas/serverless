# endpoints:
 - POST - https://your-api.execute-api.us-east-1.amazonaws.com/dev/todos
 - GET - https://your-api.execute-api.us-east-1.amazonaws.com/dev/todos
 - GET - https://your-api.execute-api.us-east-1.amazonaws.com/dev/todos/{id}
 - PUT - https://your-api.execute-api.us-east-1.amazonaws.com/dev/todos/{id}
 - DELETE - https://your-api.execute-api.us-east-1.amazonaws.com/dev/todos/{id}
# functions:
 - create: serverless-rest-api-with-dynamodb-dev-create
 - list: serverless-rest-api-with-dynamodb-dev-list
 - get: serverless-rest-api-with-dynamodb-dev-get
 - update: serverless-rest-api-with-dynamodb-dev-update
 - delete: serverless-rest-api-with-dynamodb-dev-delete
