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
 
 Usage

You can create, retrieve, update, or delete todos with the following commands:

Create a Todo

curl -X POST https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/todos --data '{ "text": "Learn Serverless" }'
Example Result:

{"text":"Learn Serverless","id":"ee6490d0-aa81-11e6-9ede-afdfa051af86","createdAt":1479138570824,"checked":false,"updatedAt":1479138570824}%
List all Todos

curl https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/todos
Example output:

[{"text":"Deploy my first service","id":"ac90fe80-aa83-11e6-9ede-afdfa051af86","checked":true,"updatedAt":1479139961304},{"text":"Learn Serverless","id":"20679390-aa85-11e6-9ede-afdfa051af86","createdAt":1479139943241,"checked":false,"updatedAt":1479139943241}]%
Get one Todo

# Replace the <id> part with a real id from your todos table
curl https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/todos/<id>
Example Result:

{"text":"Learn Serverless","id":"ee6490d0-aa81-11e6-9ede-afdfa051af86","createdAt":1479138570824,"checked":false,"updatedAt":1479138570824}%
Update a Todo

# Replace the <id> part with a real id from your todos table
curl -X PUT https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/todos/<id> --data '{ "text": "Learn Serverless", "checked": true }'
Example Result:

{"text":"Learn Serverless","id":"ee6490d0-aa81-11e6-9ede-afdfa051af86","createdAt":1479138570824,"checked":true,"updatedAt":1479138570824}%
Delete a Todo

# Replace the <id> part with a real id from your todos table
curl -X DELETE https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/todos/<id>
No output

Scaling

AWS Lambda

By default, AWS Lambda limits the total concurrent executions across all functions within a given region to 100. The default limit is a safety limit that protects you from costs due to potential runaway or recursive functions during initial development and testing. To increase this limit above the default, follow the steps in To request a limit increase for concurrent executions.

DynamoDB

When you create a table, you specify how much provisioned throughput capacity you want to reserve for reads and writes. DynamoDB will reserve the necessary resources to meet your throughput needs while ensuring consistent, low-latency performance. You can change the provisioned throughput and increasing or decreasing capacity as needed.

This is can be done via settings in the serverless.yml.

  ProvisionedThroughput:
    ReadCapacityUnits: 1
    WriteCapacityUnits: 1
In case you expect a lot of traffic fluctuation we recommend to checkout this guide on how to auto scale DynamoDB https://aws.amazon.com/blogs/aws/auto-scale-dynamodb-with-dynamic-dynamodb/
