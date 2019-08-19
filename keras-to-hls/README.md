# Keras to HLS

Here we document different keras layers that `hls4ml` supports. We also provide documentation for different example keras models (model `json` file for architecture and `hdf5` file for weights and biases) that can be translated to HLS using `hls4ml` 

## Supported layers

### General limitations:

- `keras.layers.Lambda` is currently not supported.
- Layer's operations on different axes are generally not supported (except for `Concatenate` layer), we are just using the each layer's default axis. 
- Dilations are not supported for convolutional layers.
- We currently do not support different data format (using `data_formal = "channels_last"` as default)

### Specific documentations of supported layers (including detailed limitations):

We currently support translations for the following Keras layers. Note that some layers are not fully supported, so we will also provide specific limitations for those layers here:

<details>
<summary>Core Layers</summary>
<p>

- `InputLayer`
- `Dropout`
- `Flatten`
- `Dense`:

  - `use_bias = False` is not supported.
  
- `BinaryDense`
- `TernaryDense`
</p>
</details>

<details>
<summary>Convolutional Layers</summary>
<p>

- `Conv1D`:

  - `use_bias = False` is not supported.
  - Dilations are not supported for convolutional layers
  
- `Conv2D`:

  - `use_bias = False` is not supported.
  - Dilations are not supported for convolutional layers
  
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

- `BatchNormalization`:

  - `scale = False` is currently not supported
  - `center = True` (add offset to normalized tensor) is not supported
  - Operations on different axes is not supported (always use Keras's default `axis = -1`)

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
- `Concatenate`: 

  - Concatenation is supported up to 3D. 

</p>
</details>
