# Image Captioning using Xception Netowrk and Beam Search

I tried to comment on the code as much as possible, it should be easy to follow. Feel free to use the trained model in your own projects. I have included the weight of the trained model.

### Examples of the outputs:

### Settings:

I have used a pretrained Xception network without the last two fully connected layers as the feature extractor. It outpus a 2048-d vector for each image, and this vector is fed into the LSTM network as the first activations. The LSTM network I used, consists of two layers of lstm units with 256-d hidden state. I used dropout between two lstm layers. The flicker8k dataset has been used for train and evaluation of the Image Captioner. The model reaches the BLEU score of ~57%, you can improve the score by training the model for longer durations or using a more sophisticated RNN with more layers. Also attention technique can beuse for producing the captions but I haven't tried here. I use Beam search for producing the captions.


