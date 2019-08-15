# Keras to HLS

Here we document different keras layers that `hls4ml` support. We also provide documentation for different example keras models (model json for architecture and hdf5 for weights and biases) that can be translated to HLS using `hls4ml` 

## Supported layers

We currently support translations for the following Keras layers:

### Core Layers:

- `InputLayer`
- `Dropout`
- `Flatten`
- `Dense`
- `BinaryDense`
- `TernaryDense`

### Convolutional Layers:

- `Conv1D`
- `Conv2D`

### Pooling Layers:

- `MaxPooling1D`
- `MaxPooling2D`
- `AveragePooling1D`
- `AveragePooling2D`

### Normalization Layers:

- `BatchNormalization`

### Activation Layers:

- `Activation`
- `LeakyReLU`
- `ThresholdedReLU`
- `ELU`
- `PReLU`

### Merge Layers:

- `Add`
- `Subtract`
- `Multiply`
- `Average`
- `Maximum`
- `Minimum`
- `Concatenate`

## Example models
