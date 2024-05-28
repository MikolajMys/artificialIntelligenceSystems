```python
import matplotlib.pyplot as plt
import numpy as np 

class Neuron:
    def __init__(self, n_inputs, bias = 0., weights = None):
        self.b = bias
        if weights: self.ws = np.array(weights)
        else: self.ws = np.random.rand(n_inputs)

    def _f(self, x): #activation function (here: leaky_relu)
        return max(x*.1, x)

    def __call__(self, xs): #calculate the neuron's output: multiply the inputs with the weights and sum the values together, add the bias value,
        # then transform the value via an activation function
        return self._f(xs @ self.ws + self.b)

class Layer:
    def __init__(self, neurons, n, weights=None):
        self.neurons = [Neuron(n, weights) for _ in range(neurons)]
    def get_value(self, inputs):
        return [neuron(inputs) for neuron in self.neurons]

class Neuron_Network:
    def __init__(self, layers, sizes, weights=None):
        self.layers = []

        for i in range(1, layers):
            self.layers.append(Layer(sizes[i], sizes[i - 1], weights))

    def resume(self, i):
        for layer in self.layers:
            i = layer.get_value(i)
        return i




class Main:
    #sth
```
