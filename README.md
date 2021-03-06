# Image-Captioning

It is an artificial intelligence problem where a textual description is generated for a given photograph. It requires both methods from computer vision to extract features from the image and a sequence language model to understand and represent linguistic features of the Text Data.

I fine-tuned the pre-trained VGG16 model to extract features from the image (13 CNN + 3 FC), and the GRU Sequence model was used to encode linguistic features and Generate word sequences. In this project, I used Flickr8k Dataset containing 8000 images in JPEG format and multiple text descriptions corresponding to each photograph.

The model was built and trained in Tensorflow. The VGG-16 model takes a photo input and produces a feature vector of 4,096 elements. An FC Dense layer processes these features to produce a 256 element representation of the image. The Sequence model expects input sequences with a length of 25 words which are fed into a Word Embedding layer with 256 Embedding Dimension. It is followed by a GRU layer with 256 memory units. The input models used 50% Dropout Regularization to prevent Overfitting and finally produced a 256 element vector. Features from both the Input models were merged using a Keras addition layer. This is then fed to another Dense Layer with 256 neurons and then to a final output Dense layer that makes a SoftMax prediction over the entire vocabulary to predict the next word in the sequence.

The actual and predicted descriptions are collected and evaluated collectively using the BLEU score that summarizes how close the generated text is to the expected text. BLEU scores are used in text translation for evaluating translated text against one or more reference translations.
