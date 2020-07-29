
# Transformer from scratch.

REF :
[Modern Natural Language Processing in Python | Udemy](https://www.udemy.com/course/modern-nlp/) 


1. Transformers are sequence to sequence language models. Typically used in language translations, text generation, summarization, chatbots etc.
2. Old fashioned NLP : (with RNNs) : Encoder used to summarize all the input sequence info and decoder used to take input this final hidden state info from encoder. The information in the beginning is faded.
3. All you need is Attention : To overcome the loss of info, a new global context vector is created using all the hidden states of encoder. 

4. Attention in Transformer : Attention says how the current state of decoder is related to our global input sequence.
 ![Context_Vector_Image](https://user-images.githubusercontent.com/16293041/88809285-910ade00-d1d1-11ea-8999-b9614d193806.png)
 
 ci = weighted sum of all h(hidden states)
 
 <img src="https://user-images.githubusercontent.com/16293041/88809186-733d7900-d1d1-11ea-92e2-675c479785c6.png" width="200">
 
 We apply softmax function to create weights for weighted sum which is alpha.
 
 Coefficient e is the similarity between hidden states of all encoder and hidden states of all decoders. 
 The way similarity is computed between hidden states of encoder(h) and hidden states of decoder(g) is by a function.
 Any similarity function would do, that can compute the current state of decoder by computing how the previous hidden state of decoder is related to each state of encoder.
 Now that we have those similarity weights (e), we just apply softmax to have real weights that we can use for weighted sum (alpha).
 Now we apply those weights to all the hidden states of the encoder (h) to get the context vector c. So, this c vector is made of hidden states of encoder which are related to current state of decoder.
 

5. Encoding for Transformer :
6. Transformer Architecture details :

# Transformer - Application.
English- French Translator




