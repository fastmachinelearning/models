# Keras to HLS

Here we document different keras layers that `hls4ml` support. We also provide documentation for different example keras models (model json for architecture and hdf5 for weights and biases) that can be translated to HLS using `hls4ml` 

## Supported layers

We currently support translations for the following Keras layers:

<details>
<summary>Core Layers</summary>
<p>
  
- `InputLayer`
- `Dropout`
- `Flatten`
- `Dense`
- `BinaryDense`
- `TernaryDense`
</p>
</details>

<details>
<summary>Convolutional Layers</summary>
<p>

- `Conv1D`
- `Conv2D`
</p>
</details>

<details>
<summary>Pooling Layers</summary>
<p>

- `MaxPooling1D`
- `MaxPooling2D`
- `AveragePooling1D`
- `AveragePooling2D`
</p>
</details>

<details>
<summary>Normalization Layers</summary>

- `BatchNormalization`
</p>
</details>

<details>
<summary>Activation Layers</summary>
</p>

- `Activation`
- `LeakyReLU`
- `ThresholdedReLU`
- `ELU`
- `PReLU`
</p>
</details>

<details>
<summary>Merge Layers</summary>
</p>

- `Add`
- `Subtract`
- `Multiply`
- `Average`
- `Maximum`
- `Minimum`
- `Concatenate`
</p>
</details>

## Example models

Here we provide detailed documentations for our example Keras models with regard to their architecture, inputs and predictions. All of the example model `json` and `h5` files are stored in `example-keras-model-files`
### [1 layer model](./example-keras-model-files/1-layer-model/)

<details>
  </p>
  
  #### Architecture:
  
  This model has 385 parameters in total. 
  
  #### Example inputs and expected predictions:
  
  
  </p>
</details>

### 3-layer models
