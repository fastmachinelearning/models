# Keras to HLS

Here we document different keras layers that `hls4ml` supports. We also provide documentation for different example keras models (model `json` file for architecture and `hdf5` file for weights and biases) that can be translated to HLS using `hls4ml` 

## Supported layers

### General limitations:

- `keras.layers.Lambda` is currently not supported.
- Layer's operations on different axes are generally not supported (except for `Concatenate` layer), we are just using the each layer's default axis. 
- Dilations are not supported for convolutional layers.
- We currently do not support different data format (using `data_formal = "channels_last"` as default)
- Some layers supported here (e.g `BinaryDense` and `TernaryDense`) are not implemented in the main Keras distribution. If you want to use them refer to [here](https://github.com/hls-fpga-machine-learning/keras-training/tree/master/layers) for detailed implementation. 

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
  
- `BinaryDense`:

	- not implemented in the main Keras distribution, refer to [here](https://github.com/hls-fpga-machine-learning/keras-training/tree/master/layers) for more details. 
	
- `TernaryDense`:

	- not implemented in the main Keras distribution, refer to [here](https://github.com/hls-fpga-machine-learning/keras-training/tree/master/layers) for more details. 
	
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

## Model testing

We carried out models testing using configuration given as in the example [configuration file](https://fastmachinelearning.org/hls4ml/setup/CONFIGURATION.html)). Here are documentations of which models synthesize sucessfully and which don't under those specific configurations. Note that we carried out the testing in vivado verison 2018.2):

- `KERAS_1layer`: all models synthesized sucessfully with out-of-the-box configuration.
- `KERAS_3layer`: all models synthesized sucessfully with out-of-the-box configuration.
- `KERAS_conv`: all models except for `KERAS_conv1d.json` and  `KERAS_conv2d_model.json` (this model works for vivado version 2017.2).
- `KERAS_dense`: model `KERAS_dense_16x100x100x100x100x100x5.json` synthesize sucessfully, note that one has to specify `Strategy: resource` and use a large reuse factor (we used 2000) in the configuration in order for the models to synthesize. Other models does not synthesize using current master branch.
**NOTE:** If you really need to sythesize bigger dense model, you can install an older version of `hls4ml` from [this branch](https://github.com/hls-fpga-machine-learning/hls4ml/tree/nvt/large_mlp_wDep_v6). The tutorial on how to use the older model can be found [here](https://github.com/FPGA4HEP/course_material/blob/paris/part1_hls4ml_intro.md). 
- `jetTagger`: all models does NOT synthesize (might work on vivado version 2017.2).
- `KERAS_bnn`(binary neural network): all models synthesized sucessfully with out-of-the-box configuration.
