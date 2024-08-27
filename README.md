# SignatureTester

Készült a BME BSC önálló laboratórium 2023
Aláírás hitelesítés projekt keretén belül - Created for the BME Bsc indipendent laboratory signiture authentication project 2023

## Setup
The project can be opened with the Jupyter notebook. 
To run it you need to install the iisignature, numpy, sklearn, tqdm and torch libraries.

## Configuration
**You can configure these values to achive the desired performance:**
- ws = 20 (The window size in of the input which is fed to the RNN at once)
- signiture_level = 5 (The path signiture level)
- TESTPERCENTAGE = 10 (From the whole database how many datapoints should be reserved for testing)
- epochs = 400 (The count of the learning iterations)
- hidden_size = 128 (The neuron count inside 1 RNN layer)
- num_layers = 3 (The number of RNN layers)
- batch_size = 10 (The number of iteration after we recalculate the weights)

# Database
I used the [SVC2004](https://cse.hkust.edu.hk/svc2004/) database to train and test my model.

# Data preprocessing
1. The database is loaded with numpy
2. Every signiture has to be split up to multiple equally sized parts (window size)
3. The parts must go through a path signiture algorythm to extract the useful features
4. The datas are normalized with a Standard scaler algorythm
5. As a last step we need to shuffle the data. (We need to be carefull to shuffle the valid output as well equaly)

# Neural Network
The RNN neural network is a type of machine learning algorythm were the output from 1 iteration is then given back to the next iteration as an input.
The loss function is the triplet loss algorythm. You can read more about it in [this](https://towardsdatascience.com/triplet-loss-advanced-intro-49a07b7d8905?gi=8a3371524a4a) article.

# Results
False acceptance rate: 9% <br>
False rejection rate: 4% <br>
The learning took about 20 mins with an RTX2060 GPU

# Subscript
The basis of this implementation was this article: **_LAI, Songxuan; JIN, Lianwen; YANG, Weixin. Online signature 
verifica on using recurrent neural network and length-normalized path signature descriptor. In: 2017 
14th IAPR interna onal conference on document analysis and recogni on (ICDAR). IEEE, 2017. p. 400
405._**
