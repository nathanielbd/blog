---
title: "Making a Neural Network from Scratch"
date: 2020-09-14T11:54:31-05:00
images:
draft: true
tags: 
  - SASE Labs
  - Machine Learning
---

*This content was created as part of an educational workshop for [SASE Labs UMN](https://SASE-Labs-2021.github.io), of which I served as director from 2020-2021. It is partially based on [Introduction to Machine Learning by Ethem Alpaydin](https://www.cmpe.boun.edu.tr/~ethem/i2ml2e/index.html)*

# Context

## Making?

Yes. I mean programming, training, and testing on classifying handwritten digits.

## Neural Network?

A biologically inspired computing framework.

| ![](https://www.researchgate.net/profile/Paulo_Cantillano/publication/338607457/figure/fig4/AS:847615730130946@1579098746720/A-biological-neuron-left-and-its-mathematical-model-right-Konate-2019.jpg) |
|:--:|
| Stanford CS231N's analogy |

You may know that biological neurons propogate action potentials carried by ions. They also operate on an all-or-none principle; if a stimulus does not exceed the threshold potential, no response is given. Otherwise there is a full response.

This is reflected in our model. The stimuli of a neuron is the data (entries in a  vector): \\(\begin{bmatrix}x_0\\\x_1\\\\\vdots\\\x_n\end{bmatrix}\\). In our biological analogy, an entry in the vector is like an incoming action potential from another neuron.

Associated with each stimuli is a weight (\\(w_i\\)) which corresponds to how sensitive the neuron is to that stimulus (\\(x_i\\)). Changing these weights is how our neural network will 'learn.' 

Of course, the neuron needs to take all of these stimuli and output either a single full response or virtually no response. To consolidate the stimuli into a single value, we multiply each stimulus by its corresponding weight and add each product together. You may know this as a dot product:

$$\begin{bmatrix}x_0\\\x_1\\\\\vdots\\\x_n\end{bmatrix}
\cdot \begin{bmatrix}w_0\\\w_1\\\\\vdots\\\w_n\end{bmatrix}
= w_0 x_0 + w_1 x_1 + \dots + x_n w_n$$

After this dot product, we add a bias term (\\(b\\)). It is analogous to a biological neuron's threshold potential. In practice, this is a constant so that the weights can be changed relative to it.

In order to achieve all-or-none behavior like a real neuron, we feed this single value into what's called an 'activation function' (\\(f\\)). As you may guess, these functions often return zero for small values and a positive number for large values.

| ![](https://miro.medium.com/max/1050/1*ZafDv3VUm60Eh10OeJu1vw.png) |
|:--:|
| Some activation functions |

We will make a feed-forward neural network. It has neurons organized into layers. The neurons receive the signals from the previous layer and send their activation values to the next layer.

| ![](https://www.asimovinstitute.org/wp-content/uploads/2019/04/NeuralNetworkZoo20042019.png) |
|:--:|
| There are several other neural network architectures |

## From Scratch?

Only using python and numpy. Familiarity with linear algebra and multivariable calculus is very helpful, but not absolutely necessary.

# The Program

Let's make a feed-forward neural network with one hidden layer (one layer between the data and the output). [It's been proven](http://cognitivemedium.com/magic_paper/assets/Hornik.pdf) that this is enough to learn any nonlinear function of the input. [Michael Nielsen has a cool visualization of this proof](http://neuralnetworksanddeeplearning.com/chap4.html).

It's also small enough to diagram.

| ![](/nn/diagram.png) |
|:--:|
| A simple neural network |


## Variables

- \\(V\\): the weights on the hidden layer activation to the output layer
    - indexed \\(v_{ih}\\) to indicate which output neuron and hidden neuron to which it's connected
- \\(W\\): the weights on the data layer to the hidden layer
    - indexed \\(w_{hj}\\) to indicate which hidden neuron and data "neuron" to which it's connected
- \\(X\\): the input layer
    - indexed \\(x_j\\). You can think of them as a dimension or factor of the data.
- \\(Y\\): the output layer
- \\(Z\\): the hidden layer

| {{< rawhtml >}} <video controls width="80%"><source src="/nn/NetworkPieces.mp4"></video> {{< /rawhtml >}} |
|:--:|
| The same neural network, broken down |

Just keep in mind the computer doesn't have this complex wiring diagram interally; it just multiplies matrices.

| |
|:--:|
| POV you're a computer |

## Pseudocode

```
randomly initialize V and W
while not converged
  for t from 0 to count(X)
    for h from 0 to H
      Z[t, h] := f(W[,h] dot X[t])
    for i from 0 to K
      Y[t, i] := V[,i] dot Z[t]
    Y[t] := softmax(Y[t])
    for i from 0 to K
      dV[,i] := eta * (r_it - Y[t, i]) *Z[t]
    for h from 0 to H
      dW[,h] := f(eta * sum((r_it - Y[t][i])*V[h][i] for i from 0 to K)*X[t])
    V := V + dV
    W := W + dW
end
```