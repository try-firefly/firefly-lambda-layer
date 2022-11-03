A Lambda layer to assist in Open Telemetry trace instrumentation.
To be used in conjunction with the AWS managed Open Telemetry layer.
Uses a custom handler which wraps the user defined handler.

- If incoming `event` has `messageAttributes.traceparent`, uses the `stringValue` of `traceparent` to parse parent context and reassigns it in autoinstrumented span
- If need to invoke lambda, use require `/opt/nodejs/lambda-invoke.js` and use exported `invokeLambda` function. Given `params` should follow AWS SDK's format.
  - TODO: switch to require-in-the-middle implementation for aws-sdk

## Instructions to build layer:

In the root directory, run the following command:

```
zip -r firefly-layer-demo.zip ./*
```
