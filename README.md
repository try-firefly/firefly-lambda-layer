A Lambda layer to assist in Open Telemetry trace instrumentation and context propagation.
To be used in conjunction with the AWS managed Open Telemetry layer.
Uses a custom handler which wraps the user defined handler.

## Functionality

- If incoming `event` has `messageAttributes.traceparent`, uses the `stringValue` of `traceparent` to parse parent context and reassigns it in autoinstrumented span
- If need to invoke lambda, use require `/opt/nodejs/lambda-invoke.js` and use exported `invokeLambda` function. Given `params` should follow AWS SDK's format.
  - TODO: switch to require-in-the-middle implementation for aws-sdk

## Instructions to build layer:

In the root directory, run the following command on Linux:

```
bash build.sh
```

## Limitations

- Context propagation for Lambda A invoking Lambda B results in a span from Lambda B that is a sibling to the Lambda invocation span from Lambda A, not a child span (as one would expect)
