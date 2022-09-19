# AUDIO_SUPER_RESOLUTIO
We proposed an auto-encoder model which has two main modules: Encoder and Decoder.
Equal number of encoding and decoding blocks are present. In between encoder and decoder
a bottleneck layer is present. There are skip connections between the layers of encoder and
decoder<br />

Encoder: In encoder the downsampling of input signal occurs. Each block consists of two
components: Dilated convolution and ReLu activation function. Dilated convolution is used
for feature extraction.<br />

Decoder: In decoder the upsampling of input signal occurs. Each block consists of five
components: Dilated convolution, ReLu activation function, Dropout, subpixel shuffling layer
and stacking. Dilated convolution is used for feature extraction and for enhancing the features
extracted by downsampling blocks.<br />

Bottleneck architecture: The model contains B successive downsampling and upsampling
blocks. Each block performs convolution, batch normalization, and uses leaky ReLu activation
function. Downsampling block b = 1, 2, ..., B contains max(2(6+b)
, 512) convolutional filters
of length min(2(7b) + 1, 9) and a stride of 2. Upsampling block b has max(2(7+(Bb+1)
, 512)
filters of length min(2(7+(Bb+1)
, 9).<br />

Skip connections: To increase the speed of the training and reduce the data loss, the model
can learn only y-x.<br />

Subpixel shuffling layer: The mapping of an input tensor of dimension F ×d into one of size
F/2×d is done by upsampling block’s convolution layers. The subpixel layer reshuffles F/2x2d
to tensor of size F/4×2d.These are concatenated with F/4 features from the downsampling
stage in order to get the desired output of size F/2 × 2d.<br />

Dilated Convolution: Dilated Convolution is a type of convolutional layer for expanding
the kernel (input) by introducing holes between its parts. It is same as convolution, but
with sample skipping to cover a broader region of the input. An additional parameter called
dilation rate(l) tells how much the receptive field is expanded. Depending on the value of
l, inputs are skipped.Using dilated convolution increases the receptive field and gives more
information about the input in the same computation cost.
