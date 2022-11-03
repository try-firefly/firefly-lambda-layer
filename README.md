A Lambda layer to assist in Open Telemetry trace instrumentation.
To be used in conjunction with the AWS managed Open Telemetry layer.
Uses a custom handler which wraps the user defined handler.

- If incoming `event` has `messageAttributes.traceparent`, uses the `stringValue` of `traceparent` to parse parent context and reassigns it in autoinstrumented span

## Instructions to build layer:

In the root directory, run the following command:

```
zip -r firefly-layer-demo.zip ./*
```
