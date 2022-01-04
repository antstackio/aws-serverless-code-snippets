# AWS Serverless Code Snippets

With the use of this extension, you can increase your speed of creating AWS service functions with single command. This project is an open-source project.

## Features

- You can create simple AWS Service functions with a single command. We have created snippets for AWS S3, SQS, and SNS services for now.

- Use `Tab->` to jumping between the highlighted texts to edit the text as per your desires

  ![SAMPLE](https://github.com/antstackio/aws-serverless-code-snippets/raw/master/gifs/sample.gif)

## Requirements

Before Install this VSCode Extension for AWS Code Snippet. Please install AWS-SDK in your local. By running this command.

```
npm install aws-sdk
```

## Supported language (file extensions)

- Javascript (.js)

<br>

## Snippet info

#### Basic Snippets

|  Prefix | Method                                                                 |
| ------: | -----------------------------------------------------------------------|
| `cas3→` | `const AWS = require('aws-sdk');`,`const s3 = new AWS.S3()`            |
| `casq→` | `const AWS = require('aws-sdk');`,`const sqs = new AWS.SQS()`          |
| `casn→` | `const AWS = require('aws-sdk');`,`const sns = new AWS.SNS()`          |
| `cadb→` | `const AWS = require('aws-sdk');`,`const db = new AWS.DynamoDB()`      |
| `casf→` | `const AWS = require('aws-sdk');`,`const sf = new AWS.StepFunctions();`|

### `!s3Upload`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_Name",
    Keys: "file_path",
    Expires: "bucket_expire_time",
  };
  try {
    const variable1_s3_data = await s3.putObject(Bucket_params).promise();
    console.log("S3 Data ", variable1_s3_data);
    return variable1_s3_data;
  } catch (error) {
    console.error("Put Object to S3 :", error);
    return error;
  }
};

```

### `!s3List`

```
const function_name = async () => {
  const Parameter_For_Bucket = {
    Bucket: "Bucket_name",
    Prefix: "path_name/",
  };
  try {
    const variable_to_store_data = await s3
      .listObjectV2({ 2: Parameter_For_Bucket })
      .promise();
    const variable_to_return = variable_to_store_data.Contents;
    return variable_to_return;
  } catch (error) {
    console.error("Get Object from S3 :", error);
    return error;
  }
};

```

### `!s3Get`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_Name",
    Keys: "file_path",
  };
  try {
    const variable1_s3_data = await s3.getObject(Bucket_params).promise();
    console.log("S3 Data ", variable1_s3_data);
    return variable1_s3_data;
  } catch (error) {
    console.error("Get Object from S3 :", error);
    return error;
  }
};


```

### `!s3UWM`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_Name",
    Keys: "file_path",
    Expires: "bucket_expire_time",
    Metadata: {
      metadata1: "value1",
    },
  };
  try {
    const variable1_s3_data = await s3.putObject(Bucket_params).promise();
    console.log("S3 Data ", variable1_s3_data);
    return variable1_s3_data;
  } catch (error) {
    console.error("Put Object to S3 :", error);
    return error;
  }
};

```

### `!s3C`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Destination_Bucket_Name",
    CopySource: "Source_Bucket_name/",
    Keys: "file_path",
  };
  try {
    const variable1_s3_data = await s3.copyObject(Bucket_params).promise();
    console.log("Copied S3 Data ", variable1_s3_data);
    return variable1_s3_data;
  } catch (error) {
    console.error("Copy Object to S3 :", error);
    return error;
  }
};

```

### `!s3Cr`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_name",
    CreateBucketConfiguration: {
      LocationConstraint: "Bucket_Region_name",
    },
  };
  try {
    const variable_1 = await s3.createObject(Bucket_params).promise();
    console.log("Bucket created in the selected region");
    return variable_1;
  } catch (error) {
    console.error("Error in Creating Bucket: ", error.stack);
    return error;
  }
};

```

### `!s3D`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_name",
  };
  try {
    const variable_1 = await s3.deleteBucket(Bucket_params).promise();
    console.log("Bucket deleted successfully......");
    return variable_1;
  } catch (error) {
    console.error("Error in Delete Bucket: ", error.stack);
    return error;
  }
};
```

### `!s3Do`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_name",
    Key: "File_path",
  };
  try {
    const variable_1 = await s3.deleteObject(Bucket_params).promise();
    console.log("Object deleted successfully......");
    return variable_1;
  } catch (error) {
    console.error("Error in Deleting Object in the Bucket: ", error.stack);
    return error;
  }
};


```

### `!s3GM`

```
const function_name = async () => {
  const Bucket_params = {
    Bucket: "Bucket_name",
    Key: "File_path",
  };
  try {
    const variable_1 = await s3.headObject(Bucket_params).promise();
    console.log(
      "Metadata from object without returning object itself",
      variable_1
    );
    return variable_1;
  } catch (error) {
    console.error(
      "Error in getting metadata of the object in the Bucket: ",
      error.stack
    );
    return error;
  }
};


```

## SQS Snippets

### `!sqsC`

```
const function_name = async () => {
  const SQS_Params = {
    QueueName: "Queue_name",
    Attributes: {
      QueueAttributeName_1: "Value",
    },
    Tags: {
      Tag_key: "Tag_Value",
    },
  };
  try {
    const variable_1 = await sqs.createQueue(SQS_Params).promise();
    console.log("SQS Queue is created successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS Queue creation: ", error.stack);
    return error;
  }
};


```

### `!sqsP`

```
const function_name = async () => {
  const SQS_Params = {
    QueueUrl: "Queue_name",
  };
  try {
    const variable_1 = await sqs.purgeQueue(SQS_Params).promise();
    console.log("SQS Queue is purged successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS purging queue: ", error.stack);
    return error;
  }
};


```

### `!sqsS`

```
const function_name = async () => {
  const SQS_Params = {
    MessageBody: "Message_details",
    QueueUrl: "Queue_name",
  };
  try {
    const variable_1 = await sqs.sendMessage(SQS_Params).promise();
    console.log("SQS Message send successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS send message: ", error.stack);
    return error;
  }
};

```

### `!sqsR`

```
const function_name = async () => {
  const SQS_Params = {
    QueueUrl: "Queue_name",
    MaxNumberOfMessages: "MaxNumberOfMessages_value",
    ReceiveRequestAttemptId: "ReceiveRequestAttemptId_value",
    VisibilityTimeout: "visibilityTimeout_value",
    WaitTimeSeconds: "waitTimeSeconds_value",
  };
  try {
    const variable_1 = await sqs.receiveMessage(SQS_Params).promise();
    console.log("SQS Message received successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS receive message: ", error.stack);
    return error;
  }
};

```

### `!sqsL`

```
const function_name = async () => {
  const SQS_Params = {
    MaxResults: "MaxResults_value",
    NextToken: "NextToken_value",
    QueueNamePrefix: "QueueNamePrefix_value",
  };
  try {
    const variable_1 = await sqs.listQueues(SQS_Params).promise();
    console.log("SQS listed queues successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS list queues: ", error.stack);
    return error;
  }
};
```

### `!sqsG`

```
const function_name = async () => {
  const SQS_Params = {
    QueueName: "QueueName_value",
    QueueOwnerAWSAccountId: "QueueOwnerAWSAccountId_value",
  };
  try {
    const variable_1 = await sqs.getQueueUrl(SQS_Params).promise();
    console.log("SQS Get QueueUrl successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS Get queueUrl: ", error.stack);
    return error;
  }
};
```

### `!sqsDM`

```
const function_name = async () => {
  const SQS_Params = {
    QueueUrl: "QueueUrl_value",
    ReceiptHandle: "  ReceiptHandle_value",
  };
  try {
    const variable_1 = await sqs.deleteMessage(SQS_Params).promise();
    console.log("SQS message deleted successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS Delete Message: ", error.stack);
    return error;
  }
};

```

### `!sqsDQ`

```
const function_name = async () => {
  const SQS_Params = {
    QueueUrl: "QueueUrl_value",
  };
  try {
    const variable_1 = await sqs.deleteQueue(SQS_Params).promise();
    console.log("SQS Queue deleted successfully....", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS Delete Queue: ", error.stack);
    return error;
  }
};
```

### `!sqsDLQ`

```
const function_name = async () => {
  const SQS_Params = {
    QueueUrl: "QueueUrl_value",
    MaxResults: "MaxResults_value",
    NextToken: "NextToken_value",
  };
  try {
    const variable_1 = await sqs
      .listDeadLetterSourceQueues(SQS_Params)
      .promise();
    console.log("SQS Dead LetterSourceQueues lists", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SQS ListDeadLetterSourceQueues: ", error.stack);
    return error;
  }
};

```

## SNS Snippets

### `!snsCT`

```
const function_name = async () => {
  const SNS_Params = {
    Name: "Name_value",
    Attributes: {
      Attributes_Name: "Attributes_value",
    },
    Tags: [{ Tags_Key_1: "Tags_Value_1" }],
  };
  try {
    const variable_1 = await sns.createTopic(SNS_Params).promise();
    console.log("SNS Topic created successfully...", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS Create Topic: ", error.stack);
    return error;
  }
};
```

### `!snsGT`

```
const function_name = async () => {
  const SNS_Params = {
    TopicArn: "TopicArn_value",
  };
  try {
    const variable_1 = await sns.getTopicAttributes(SNS_Params).promise();
    console.log("Get Topic Attributes", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS Get TopicAttribute: ", error.stack);
    return error;
  }
};
```

### `!snsLT`

```
const function_name = async () => {
  const SNS_Params = {
    NextToken: "NextToken_value",
  };
  try {
    const variable_1 = await sns.listTopics(SNS_Params).promise();
    console.log("List Topics", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS List Topics: ", error.stack);
    return error;
  }
};
```

### `!snsLS`

```
const function_name = async () => {
  const SNS_Params = {
    NextToken: "NextToken_value",
  };
  try {
    const variable_1 = await sns.listSubscriptions(SNS_Params).promise();
    console.log("List Subscriptions", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS List Subscriptions: ", error.stack);
    return error;
  }
};

```

### `!snsCS`

```
const function_name = async () => {
  const SNS_Params = {
    Token: "Token_value",
    TokenArn: "TokenArn_value",
    AuthenticateOnUnsubscribe: "AuthenticateOnUnsubscribe_value",
  };
  try {
    const variable_1 = await sns.confirmSubscription(SNS_Params).promise();
    console.log("Confirm Subscriptions", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS Confirm Subscriptions: ", error.stack);
    return error;
  }
};

```

### `!snsCPA`

```
const function_name = async () => {
  const SNS_Params = {
    Attributes: {
      Attribute_key: "Attribute_value",
    },
    Name: "Name_value",
    Platform: "  Platform_value",
  };
  try {
    const variable_1 = await sns
      .createPlatformApplication(SNS_Params)
      .promise();
    console.log("Create Platform application", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS Create Platform Application: ", error.stack);
    return error;
  }
};
```

### `!snsDT`

```
const function_name = async () => {
  const SNS_Params = {
    TopicArn: "TopicArn_value",
  };
  try {
    const variable_1 = await sns.deleteTopic(SNS_Params).promise();
    console.log("SNS Topic deleted Successfully", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS Delete Topic: ", error.stack);
    return error;
  }
};

```

### `!snsDPA`

```
const function_name = async () => {
  const SNS_Params = {
    PlatformApplicationArn: "  PlatformApplicationArn_value",
  };
  try {
    const variable_1 = await sns
      .deletePlatformApplication(SNS_Params)
      .promise();
    console.log("SNS Platform Application deleted Successfully", variable_1);
    return variable_1;
  } catch (error) {
    console.error("Error in SNS Delete Platform Application: ", error.stack);
    return error;
  }
};

```

## DynamoDB Snippets

### `!dbC`

```
const function_name = async () => {
  const params = {
    TableName: "`Table_name`",
    KeySchema: [
      {
        AttributeName: "`AttributeName`",
        KeyType: "`KeyType`",
      },
      {
        AttributeName: "`AttributeName`",
        KeyType: "`KeyType`",
      },
    ],
    AttributeDefinitions: [
      {
        AttributeName: "`AttributeName`",
        AttributeType: "`AttributeType`",
      },
      {
        AttributeName: "`AttributeName`",
        AttributeType: "`AttributeType`",
      },
    ],
    ProvisionedThroughput: {
      ReadCapacityUnits: `ReadCapacityUnits`,
      WriteCapacityUnits: `WriteCapacityUnits`,
    },
  };

  try {
    const variable = await db.createTable(params).promise();
    return {
      statusCode: 201,
      body: JSON.stringify({
        db_data: variable,
        message: "data created successfully in the db",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Something went wrong! check it out!",
      }),
    };
  }
};

```

### `!dbNP`

```
const dbClient = new AWS.DynamoDB.DocumentClient();

const function_name = async () => {
  const params = {
    TableName: "`TableName`",
    Item: {
      "`variable_1`": "`variable_2`",
      "`variable_3`": "`variable_4`",
    },
  };

  try {
    const function_data = await dbClient.put(params).promise();
    return {
      statusCode: 200,
      body: JSON.stringify({
        db_data: function_data,
        message: "data updated successfully in the db",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to add an item to the table! check it out!",
      }),
    };
  }
};
```

### `!dbUU`

```
const function_name = async () => {
  const params = {
    TableName: "`TableName`",
    Key: {
      "`TableVariable`": "`tableValue`",
      "`TableVariable`": "ValueVariable",
    },
    UpdateExpression: "`UpdateExpression`",
    ExpressionAttributeValues: {
      "`ExpressionAttributeValue`", // "key":"value"
    },
    ReturnValue: "UPDATED_NEW",
  };

  try {
    const variable = await dbClient.update(params).promise();
    return {
      statusCode: 200,
      body: JSON.stringify({
        db_data: variable,
        message: "data updated successfully in the db",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to update the table, check it out!",
      }),
    };
  }
};
```

### `!dbCU`

```
const dbClient = new AWS.DynamoDB.DocumentClient();

const function_name = async () => {
  const params = {
    TableName: "`TableName`",
    Key: {
      "`TableVariable`": "`tableValue`",
      "`TableVariable`": "ValueVariable",
    },
    UpdateExpression: "`UpdateExpression`",
    ConditionExpression: "`ConditionExpressionValue`",
    ExpressionAttributeValues: {
      "`ExpressionAttributeValue`", // "key":"value"
    },
    ReturnValue: "UPDATED_NEW",
  };

  try {
    const variable = await dbClient.update(params).promise();
    return {
      statusCode: 200,
      body: JSON.stringify({
        db_data: variable,
        message: "data updated successfully in the db",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to update the table, check it out!",
      }),
    };
  }
};
```

### `!dbQ`

```
const dbClient = new AWS.DynamoDB.DocumentClient();

const function_name = async () => {
  const params = {
    TableName: "`TableName`",
    KeyConditionExpression: "`ConditionExpression`",
    FilterExpression: 'FilterExpressionValues',
    ExpressionAttributeValues: {
      "`ExpressionAttributeValue`", // "key":"value"
    },
  };

  try {
    const variable = await dbClient.query(params).promise();
    return {
      statusCode: 200,
      body: JSON.stringify({
        db_data: variable.Items,
        message: "Successfully Queried the data from the table",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to query data from the table, check it out!",
      }),
    };
  }
}
```

### `!dbDI`

```
const dbClient = new AWS.DynamoDB.DocumentClient();

const function_name = async () => {
  const params = {
    TableName: "`TableNameValue`",
    Key: {
      key: "`values`",
    },
  };
  try {
    const variable = await dbClient.delete(params).promise();
    return {
      statusCode: 204,
      body: JSON.stringify({
        db_data: variable,
        message: "data deleted successfully from the db",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to delete data from the table, check it out!",
      }),
    };
  }
};
```

### `!dbG`

```
const dbClient = new AWS.DynamoDB.DocumentClient();

const function_name = async () => {
  const params = {
    TableName: "`TableNameValue`",
    Key: {
      key: "`values`",
    },
  };

  try {
    const variable = await dbClient.get(params).promise();
    return {
      statusCode: 200,
      body: JSON.stringify({
        db_data: variable.Item,
        message: "Successfully Retrieved item from DynamoDB table",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to get item from the table, check it out!",
      }),
    };
  }
};
```

### `!dbS`

```
const function_name = async () => {
  const params = {
    TableName: "`TableNameValue`",
    FilterExpression: "`FilterExpressionValue`",
    ExpressionAttributeValues: {
      "`ExpressionAttributeValue`": "`ExpressionAttributeValue`",
    },
    ProjectionExpression: "`ProjectionExpressionValue`",
  };

  try {
    const variable = await db.scan(params).promise();
    return {
      statusCode: 200,
      body: JSON.stringify({
        db_data: variable,
        message: "Successfully Retrieved data from DynamoDB table",
      }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: JSON.stringify({
        error_message: error.message,
        message: "Unable to retrieve data from the table, check it out!",
      }),
    };
  }
};
```

### `!dbDES`

```
const function_name = async () => {
  const params = {
    TableName: "`TableNameValue`",
  };

  try {
    const variable = await db.describeTable(params).promise();
    return {
      statusCode: 200,
      message: JSON.stringify({
        data: variable.Table.KeySchema,
        message: "Successfully retrieved the selected table's descriptions",
      }),
    };
  } catch (err) {
    return {
      statusCode: 500,
      message: JSON.stringify({
        error: err.message,
        message: "Unable to retrieve the selected table's descriptions",
      }),
    };
  }
};
```

### `!dbLT`

```
const function_name = async () => {
  try {
    const variable = await db.listTables({ Limit: variable }).promise();
    return {
      statusCode: 200,
      message: JSON.stringify({
        data: variable.TableNames,
        message: "Successfully retrieved the table list",
      }),
    };
  } catch (err) {
    return {
      statusCode: 500,
      message: JSON.stringify({
        error: err.message,
        message: "Unable to retrieve the table list",
      }),
    };
  }
};
```

### `!dbDT`

```
const function_name = async () => {
  const params = {
    TableName: TableNameValues,
  };
  try {
    const variable = await db.deleteTable(params).promise();
    return {
      statusCode: 204,
      message: JSON.stringify({
        data: variable,
        message: "Successfully deleted the table",
      }),
    };
  } catch (err) {
    return {
      statusCode: 500,
      message: JSON.stringify({
        error: err.message,
        message: "Error: Table not found",
      }),
    };
  }
};
```
## StepFunctions Snippets

### `!sfCA`

```
const function_name = async () => {
        const params = {
               name: `activity_name`
        };
        try {
          const variable = await sf.createActivity(params).promise();
          return  variable
 
        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Activity cannot be created "
            }
        }
      };
```
### `!sfCSM`

```
const function_name = async () => {
        const params = {
               definition: `definition`,
               name: `name`,
               roleArn: `arn`   
      /*  loggingConfiguration: { */
      /*    destinations: [ */
      /*      { */
      /*          cloudWatchLogsLogGroup: { */
      /*            logGroupArn: 'STRING_VALUE' */
      /*          } */
      /*      } */
                                               
      /*       more items  */
                                               
      /*    ] */
      /*    includeExecutionData: true || false */
      /*    level: ALL | ERROR | FATAL | OFF */
      /*  } */
      /*  tags: [ */
      /*    { */
      /*      key: 'STRING_VALUE' */
      /*      value: 'STRING_VALUE' */
      /*    } */
                                               
      /*     more items */ 
                                               
      /*  ] */
      /*  tracingConfiguration: { */
      /*    enabled: true || false */
      /*  } */
      /*    type: STANDARD | EXPRESS */
        };
        try {
          const variable = await sf.createStateMachine(params).promise();
           return  variable

        } catch (err) {
          
           return {
              error: err.message
              message: "Error: State Machine cannot be created "
             }
        }
      };
```
### `!sfDA`

```
const function_name = async () => {
        const params = {
                activityArn: `activityArn` 
        };
        try {
          const variable = await sf.deleteActivity(params).promise();
           return  variable
              
        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Activity cannot be deleted "
              }
        }
      };
```
 
### `!sfDSM`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
        };
        try {
          const variable = await sf.deleteStateMachine(params).promise();
           return  variable

        } catch (err) {
          
           return {
              error: err.message
              message: "Error: State Machine cannot be deleted "
              }
        }
      };
      
```

### `!sfDsA`

```
const function_name = async () => {
        const params = {
                activityArn: `activityArn` 
        };
        try {
          const variable = await sf.describeActivity(params).promise();
           return  variable

        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Activity cannot be described "
              }
        }
      };
      
```
### `!sfDsSM`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
        };
        try {
          const variable = await sf.describeStateMachine(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: State Machine cannot be describes "
              }
        }
      };
      
```
### `!sfDsE`

```
const function_name = async () => {
        const params = {
               executionArn: `executionArn` 
        };
        try {
          const 4:variable} = await sf.describeExecution(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Execution cannot be described" 
              }
        }
      };
```

### `!sfGAT`

```
const function_name = async () => {
        const params = {
               executionArn: `executionArn` 
        };
        try {
          const variable = await sf.getActivityTask(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot get the  Activity Task" 
              }
        }
      };
```

### `!sfGEH`

```
const function_name = async () => {
        const params = {
               executionArn: `executionArn` 
               /* includeExecutionData: true || false */
               /* maxResults: 'NUMBER' */ 
               /* nextToken: 'STRING' */
               /* reverseOrder: true || false */
        };
        try {
          const variable = await sf.getExecutionHistory(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot get the  Execution History 
              }
        }
      };
```
### `!sfLA`

```
const function_name = async () => {
        const params = {
               maxResults: `maxResults` 
               nextToken:`nextToken`  
        };
        try {
          const variable = await sf.listActivities(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot list  the Activities "
              }
        }
      };
```
### `!sfLE`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
               /* includeExecutionData: true || false */
               /* maxResults: 'NUMBER' */ 
               /* nextToken: 'STRING' */
               /* statusFilter: RUNNING | SUCCEEDED | FAILED | TIMED_OUT | ABORTED */
        };
        try {
          const variable = await sf.listExecutions(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot list  the Executions "
              }
        }
      };
```
### `!sfLSM`

```
const function_name = async () => {
        const params = {
               maxResults: `maxResults` 
               nextToken:`nextToken`  
        };
        try {
          const variable = await sf.listStateMachines(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot list  the State Machines "
              }
        }
      };
```
### `!sfLTR`

```
const function_name = async () => {
        const params = {
               resourceArn: `resourceArn` 
        };
        try {
          const variable = await sf.listTagsForResource(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot list  Tags for Resource "
              }
        }
      };
```
### `!sfRTF`

```
const function_name = async () => {
        const params = {
               taskToken: `taskToken` 
               /* cause: 'STRING' */ 
               /* error: 'STRING' */
        };
        try {
          const variable = await sf.sendTaskFailure(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot report Tasks failure "
              }
        }
      };
```
### `!sfRTH`

```
const function_name = async () => {
        const params = {
               taskToken: `taskToken` 
               /* cause: 'STRING' */ 
               /* error: 'STRING' */
        };
        try {
          const variable = await sf.sendTaskHeartbeat(params).promise();
          return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot report Tasks heartbeat "
              }
        }
      };
```
### `!sfRTS`

```
const function_name = async () => {
        const params = {
               taskToken: `taskToken` 
               /* cause: 'STRING' */ 
               /* error: 'STRING' */
        };
        try {
          const variable = await sf.sendTaskSuccess(params).promise();
          return  variable
        } catch (err) {
           return {
              message: "Error: Cannot report Tasks Success "
              }
        }
      };
```
### `!sfSE`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
               /* input: 'STRING' */ 
               /* name: 'STRING' */
               /* traceHeader: 'STRING' */
        };
        try {
          const variable = await sf.startExecution(params).promise();
          return  variable
        } catch (err) {
           return {
              message: "Error: Cannot execute this State Machine "
              }
        }
      };
};
```
### `!sfSSE`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
               /* input: 'STRING' */ 
               /* name: 'STRING' */
               /* traceHeader: 'STRING' */
        };
        try {
          const variable = await sf.startSyncExecution(params).promise();
           return  variable
        } catch (err) {
           return {
              error: err.message
              message: "Error: Cannot execute this State Machine Synchronously "
              }
        }
      };
```
### `!sfSPE`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
               /* cause: 'STRING' */ 
               /* error: 'STRING' */
        };
        try {
          const variable = await sf.stopExecution(params).promise();
           return  variable

        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Cannot stop the execution this State Machine " 
              }
        }
      };
```
### `!sfTR`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
                tags: [ /* required */
                  {
                    key:`key`
                    value: `value`
                  }
                  /* more items */       
        };
        try {
          const variable = await sf.tagResource(params).promise();
           return  variable
              
          
        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Cannot tag Resource " 
              }
        }
      };
```
### `!sfUTR`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
        tagKeys: [ /* required */
            key:`key`
          /* more items */       
        };
        try {
          const variable = await sf.untagResource(params).promise();
           return  variable
              
          
        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Cannot Untag the Resource " 
              }
        }
      };
```

### `!sfUSM`

```
const function_name = async () => {
        const params = {
               stateMachineArn: `stateMachineArn` 
       /* definition: 'STRING' */
       /*  loggingConfiguration: { */
       /*   destinations: [ */
       /*       { */
       /*         cloudWatchLogsLogGroup: { */
       /*         logGroupArn: 'STRING' */
       /*         } */
       /*      } */
       /*       more items  */
       /*    ] */
       /*    includeExecutionData: true || false */
       /*    level: ALL | ERROR | FATAL | OFF */
       /*  } */
       /*  roleArn: 'STRING' */
       /*  tracingConfiguration: { */
       /*    enabled: true || false */
       /*  } */
        }; 
        try {
          const variable = await sf.updateStateMachine(params).promise();
          return  variable
              
          
        } catch (err) {
          
           return {
              error: err.message
              message: "Error: Cannot update the StateMachine  "
              }
        }
      };
```


## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

[Code of Conduct](https://github.com/antstackio/aws-serverless-code-snippets/blob/master/CODE_OF_CONDUCT.md)

[Click Me to Convert Your code to Json](https://snippet-generator.app/?description=sample+test+&tabtrigger=&snippet=&mode=vscode)

## License

[MIT](https://github.com/antstackio/aws-serverless-code-snippets/blob/master/LICENSE)

## Release Notes

### 1.1.1

- Added dynamodb snippet templates in README file

### 1.1.0

- Added snippets for AWS DynamoDB Service

### 1.0.2

- Added Icon for the vs code extension

### 1.0.1

## Bug Fixes

- Fixed the Bucket params

### 1.0.0

## Initial Release of AWS JavaScript code snippet extension to increase productivity.

- AWS-SDK JavaScript snippets for S3 Bucket, Simple Queue Service and Simple Notification Service
