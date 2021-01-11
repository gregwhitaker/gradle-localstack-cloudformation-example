# gradle-localstack-cloudformation-example

An example of working with mock AWS CloudFormation using [LocalStack](https://github.com/localstack/localstack) and the [Gradle LocalStack Plugin](https://github.com/Nike-Inc/gradle-localstack).

In this example you will see how to configure a mock AWS environment, defined in CloudFormation, using LocalStack and
the Gradle LocalStack Plugin.

## Building the Example
Run the following command to build the example:

    ./gradlew clean build
    
## Running the Example
Follow the steps below to run the example application:

1. Run the following command to start LocalStack and initialize the environment using CloudFormation:

        ./gradlew createCFStack
        
    If successful, you will see the following in the terminal:
    
        > Task :startLocalStack
        LocalStack Started
        
        > Task :createStack
        Creating CloudFormation Stack: example-stack
        Created CloudFormation Stack: example-stack

2. Run the following command to list all CloudFormation stacks in LocalStack:

        ./gradlew listCfStacks
        
    If successful, you will see the following in the terminal:
    
        > Task :listCFStacks
        ┌─────────────────────────────────────┬────────────────────────────────────┬────────────────────────────────────┬────────────────────────────────────┐
        │StackId                              │StackName                           │StackStatus                         │CreationTime                        │
        ├─────────────────────────────────────┼────────────────────────────────────┼────────────────────────────────────┼────────────────────────────────────┤
        │arn:aws:cloudformation:us-east-1:0000│example-stack                       │CREATE_COMPLETE                     │Sun Jan 10 18:22:40 PST 2021        │
        │00000000:stack/example-stack/64c115f5│                                    │                                    │                                    │
        │-b7cc-4c70-810d-e5332c291773         │                                    │                                    │                                    │
        └─────────────────────────────────────┴────────────────────────────────────┴────────────────────────────────────┴────────────────────────────────────┘

3. Run the following command execute the example application that uses the SQS queue created by the CloudFormation template:

        ./gradlew run
        
    If successful, you will see something similar to the following in the terminal:

        > Task :run
        [main] INFO example.SqsExampleApplication - Resolved queue 'example-queue' to url: http://localhost:4566/000000000000/example-queue
        [main] INFO example.SqsExampleApplication - Sending message to 'example-queue': Example message 1
        [main] INFO example.SqsExampleApplication - Sent message: 1da27e6e-e97d-5cee-bb83-0708cc6e6eac
        [main] INFO example.SqsExampleApplication - Sending message to 'example-queue': Example message 2
        [main] INFO example.SqsExampleApplication - Sent message: 933fcf55-9ffe-4337-5259-16c0f41ef5f9
        [main] INFO example.SqsExampleApplication - Sending message to 'example-queue': Example message 3
        [main] INFO example.SqsExampleApplication - Sent message: e01dbc35-3531-0da5-0577-dc651ab39520
        [main] INFO example.SqsExampleApplication - Sending message to 'example-queue': Example message 4
        [main] INFO example.SqsExampleApplication - Sent message: 2aa505be-a97e-e945-34d9-3d0e2b360dc6
        [main] INFO example.SqsExampleApplication - Sending message to 'example-queue': Example message 5
        [main] INFO example.SqsExampleApplication - Sent message: 09cea2be-6db5-b3ee-6e93-6d030c694e12
        [main] INFO example.SqsExampleApplication - Receiving messages from 'example-queue'...
        [main] INFO example.SqsExampleApplication - Received message: Example message 1
        [main] INFO example.SqsExampleApplication - Receiving messages from 'example-queue'...
        [main] INFO example.SqsExampleApplication - Received message: Example message 2
        [main] INFO example.SqsExampleApplication - Receiving messages from 'example-queue'...
        [main] INFO example.SqsExampleApplication - Received message: Example message 3
        [main] INFO example.SqsExampleApplication - Receiving messages from 'example-queue'...
        [main] INFO example.SqsExampleApplication - Received message: Example message 4
        [main] INFO example.SqsExampleApplication - Receiving messages from 'example-queue'...
        [main] INFO example.SqsExampleApplication - Received message: Example message 5
    
## Bugs and Feedback
For bugs, questions, and discussions please use the [Github Issues](https://github.com/gregwhitaker/gradle-localstack-cloudformation-example/issues).
         
## License
MIT License

Copyright (c) 2021 Greg Whitaker

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.