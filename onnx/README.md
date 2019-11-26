# ONNX 

## Model testing

Testing with vivado 2018.2

- `conv1d`: all models synthesized successfully with out-of-the-box configuration. 

- `conv2d`: all models do NOT synthesize with out-of-the-box configuration. (This issue is likely due to vivado version, the models might work with vivado 2017.2)

- `dense`: `dense_big_keras.onnx` requires large reuse factor used with `strategy:resource` in the configuration. 

- `three_layer`: all models synthesize successfully with out-of-the-box configuration. 

- `two_layer`: all models synthesize successfully with out-of-the-box configuration. 