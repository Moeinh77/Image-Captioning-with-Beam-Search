# Generating image captions using Xception Network and Beam Search

I tried to comment on the code as much as possible, it should be easy to follow. Feel free to use the trained model in your own projects. I have included the weight of the trained model. The model reaches the BLEU score (explained in further section) of ~57% for uni-grams on test set, you can improve the score by training the model for longer durations or using a more sophisticated RNN with more layers. If you look at the examples below, you observe that the model is pretty good at recognizing the actions but makes some mistakes at recognising the colors. Beam search with beams of 1,3, and 5 have been tested. Also, I tried using sum of the log of probabilities in beam search and result imporoved a little bit for some samples of the test set as shown below.

### Examples of the outputs:

![](results_modelv2.png)

### Settings:

I have used a pretrained Xception network without the last two fully connected layers as the feature extractor. It outpus a 2048-d vector for each image. The extracted vector of the picture is fed to the decoder both with the input at each step and also as hidden state of the first cell.. The GRU network I used, consists of two layers of GRU units with 256-d hidden state. I used dropout between two GRU layers. The Flickr8k dataset has been used for train and evaluation of the Image Captioner. Moreover, attention technique can be used for producing the captions but I haven't tried here. I use Beam search for producing the captions.

### Model: 

![](model_v2.png)

### Metric:

The primary programming task for a BLEU implementor is to compare n-grams of the candidate with the n-grams of the reference translation and count the number of matches. These matches are position-independent. The more the matches, the better the candidate translation is.

### More on image captioning:

:notebook: [Show and Tell: A Neural Image Caption Generator](https://arxiv.org/abs/1411.4555)

:notebook: [Show, Attend and Tell: Neural Image Caption Generation with Visual Attention](https://arxiv.org/abs/1502.03044)

:notebook: [Automated Image Captioning with ConvNets and Recurrent Nets](https://cs.stanford.edu/people/karpathy/sfmltalk.pdf)
