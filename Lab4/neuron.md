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
    def __init__(self):
        self.positions = []
        (self.fig, self.ax) = plt.subplots()
        self.layer = Layer(3, 2)
        self.sizes = [3, 4, 4, 1]
        self.layers = len(self.sizes)
        self.up_dist = 1.0 / max(self.sizes)
        self.down_dist = 1.0 / (self.layers - 1)
        self.neuron_network = Neuron_Network(self.layers, self.sizes)

    def produce_neurons(self):
        for i, size in enumerate(self.sizes):
            positions_of_layer = []
            for j in range(size):
                x = i * self.down_dist
                y = (j - size / 2) * self.up_dist + 0.5 + 0.07
                positions_of_layer.append((x, y))
                r = 0.06
                neuron = plt.Circle((x, y),
                                    r, facecolor='white',
                                    edgecolor='black',
                                    linewidth=1.3,
                                    zorder=1.5)
                self.ax.add_patch(neuron)

                if i == 0:
                    color = 'red'
                    y = self.up_dist * self.sizes[0] + 0.05
                    xy = ((x - r) - 0.02, 0)
                elif i == self.layers - 1:
                    color = 'green'
                    y = self.up_dist * self.sizes[0] - 0.45
                    xy = ((x - r) - 0.02, 0.25)
                else:
                    color = 'blue'
                    y = self.up_dist * self.sizes[0] + 0.15
                    xy = ((x - r) - 0.02, 0)
                    if j == 0:
                        self.ax.text(x-0.07, -0.1, 'hidden\nlayer', weight='bold', color='blue')

                border = plt.Rectangle(xy, r * 2 + 0.04, y, color=color, zorder=0)
                self.ax.add_patch(border)

                if i == 0:
                    neuron.set_facecolor('white')
                    neuron.set_edgecolor('black')
                    if j == 0:
                        self.ax.text(x-0.07, 0.01, 'input\nlayer', weight='bold', color='white')

                if i == self.layers - 1:
                    neuron.set_facecolor('white')
                    neuron.set_edgecolor('black')
                    if j == 0:
                        self.ax.text(x-0.07, 0.27, 'output\nlayer', weight='bold', color='white')

            self.positions.append(positions_of_layer)

    def draw_connections(self):
        for i in range(len(self.positions) - 1):
            for (x1, y1) in self.positions[i]:
                for (x2, y2) in self.positions[i + 1]:
                    self.ax.plot([x1, x2], [y1, y2], 'darkgray', zorder=1)

    def show_plot(self):
        self.ax.axis('off')
        plt.show()

    def run(self):
        self.produce_neurons()
        self.draw_connections()
        self.show_plot()

main = Main()
main.run()
```
