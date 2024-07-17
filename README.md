# Stock-Model-Prediction
In this demonstration, we will compare Long Short-Term Memory (LSTM) models with Recurrent Neural Network (RNN) models. While both are types of neural networks designed for sequential data, they have distinct functions and applications. We will use Microsoft stock data from Yahoo Finance to analyze these differences.

For further reading on RNNs and LSTMs, please refer to the following resources:

LSTM: https://colah.github.io/posts/2015-08-Understanding-LSTMs/

RNNs: https://www.geeksforgeeks.org/introduction-to-recurrent-neural-network/

# Explaining the data 
Before analyzing the models, we must understand the data. The models make predictions based on the stock's closing prices, which are scaled from their original range to a 0-1 range to ensure efficient and stable training. We split the data into 80% training and 20% testing sets, with a 60-day overlap to maintain a continuous sequence. The 60-day sequences serve as inputs, while subsequent prices are the outputs. This preprocessing step ensures that the models operate effectively and efficiently.

# What is an RNN 
Recurrent Neural Networks (RNNs) are specialized neural networks designed for processing sequential data, such as time series and natural language. What sets RNNs apart from traditional neural networks is their ability to maintain a memory of previous inputs through a hidden state. This memory allows RNNs to consider the sequence context when making predictions or classifications. At each time step in the sequence, the RNN computes a hidden state based on the current input and the previous hidden state, using shared weights across all time steps. This weight sharing reduces the number of parameters in the model and enhances its ability to generalize.

However, RNNs face challenges such as vanishing and exploding gradients, which can hinder their ability to learn long-term dependencies effectively. Variants like Long Short-Term Memory (LSTM) networks and Gated Recurrent Units (GRU) have been developed to mitigate these issues, providing more sophisticated mechanisms for handling long-range dependencies in sequential data. RNNs find applications in diverse fields including natural language processing, speech recognition, time series prediction, and music generation, where understanding and leveraging sequential patterns are crucial.

# What is an LSTM 
Long Short-Term Memory (LSTM) models are a sophisticated type of RNN designed to remember long-term dependencies. LSTMs incorporate a memory cell and three gates (input, forget, and output gates) to manage information flow. The input gate determines what information is added to the memory cell, the forget gate decides what information to discard, and the output gate presents the relevant information. This architecture allows LSTMs to effectively manage long-term dependencies in sequential data.

The Architecture is really what makes this process possible. There are three gates in the memory cell( this is labeled as cellState in the model): forget gate, output gate, and input gate. The input gate controls what memory is added to the memory cell. The forget gate controls what information is stored or removed. This is done by multiplying two inputs through weight matrices, followed by the bias and squeezed by the activation function. Then if the output is 1 it is remembered, if it is 0 then its forgotten. Finally, the output gate presetns this to the user. These all form a chain-like structure.

# Looking at the two models
When looking at the two models it is important to analyze the numbers because the visiual differnce may not be as large. Looking at each loss in the epochs are important in understanding how the LSTM and RNN predictions are different. In summary, while RNNs and LSTMs share the ability to process sequential data, their architectures and mechanisms for handling memory and gradients differ significantly. These differences lead to variations in performance and predictive accuracy across different applications, with LSTMs typically outperforming RNNs in tasks requiring robust memory retention and accurate long-term predictions.

# Architecture
There are four behavior types of RNNs. The first one is one-to-one, this type of RNN behaves the same as any simple neural network it is also known as a vanilla neural network, in which there is only one input and one output. Next is one-to-many where there is only one input and many outputs associated with it, an example of this would be image captioning because you feed the machine one input image but there are many possibilities for a caption. Next, there is many-to-one where many inputs are fed to the network at several states but the network generates only one output, an example of this would be sequential analysis. Lastly, many-to-many is multiple inputs and multiple outputs corresponding to a problem, an example of this would be language translation. When talking about the architecture, RNNs have the same layout as basic neural networks but the difference is the way information flows, which depends on the type of RNN we are looking at.

As mentioned before memory cells are the special part of LSTMs that allow for them to store the long-term dependencies by holding information for an extended period. This is possible using three gates, including an input gate, an output gate, and a forget gate. The input gate controls what memory is added to the memory cell. The forget gate controls what information is removed from the memory gate by multiplying two inputs through weight matrices, followed by the bias addition, and then the activation function squeezes the product. The result is normally a 1 or 0, if the information is 1 then it is stored for previous use, if a 0 then it is forgotten. Finally, the output gate is tasked with extracting useful information from the previous outputs and presenting it as an output for the users. Just like regular RNNs, LSTMs have a hidden state that is updated based on the inputs, the previous hidden states, and the memory cell’s current state. All of these together form a chain-like structure.

# How is it doing this?
These applications rely on the history of their user’s input to logically give a response to the user’s questions. This is achieved by the unique process of these networks. The sharing of parameters across each layer of the network and hidden states is what makes this possible. Unlike regular neural networks where the weights are different in every node, RNNs keep a consistent weight across the board. Even though the weights are the same, these are still adjusted through the process of backpropagation and gradient descent to support reinforcement learning. A difference between the MLPs and RNNs is that they use backpropagation through time (BPTT) to analyze gradients. The difference between backpropagation and BPTT is when each variable is computed one at a time in a specified order, for example first hidden state 1 and hidden state 2 and then hidden state 3 and so on, then all this will be applied throughout all these hidden time states in order. However, you are probably wondering, what is this hidden state?
A hidden state is what allows the RNNs to remember the patterns of the sequential data which allows it to make predictions based on the previous outputs. Not only does the hidden state separate RNNs from MLPs because of their ability to remember but it also reduces the complexity making it easier to understand. This is achieved through what we just discussed, but like every other neural network, many equations come along with it. Through these hidden states, there are activation functions that are passed along these states, typically tanh. Below I provided a picture that shows these equations broken down.


# Predicted Model
The below graph includes the prices of the stocks in the past that the model was observing and then shows the prices of the predicted stocks by the model. These are added into one continous line but seperated by color. As mentioned before, the actual code is shown on the medium website link showed above.

