# minigrad

A mini version of Pytorch neural network nn.module and backpropagation. The library includes an object called "Numnum" (why not?) that automates the backpropagation process in its raw form over a dynamically built Directed Acyclic Graph. Results can be tested against Pytorch backpropagation for reference.

# Usage

```
from minigrad.lib import Numnum

a = Numnum(-1.0)
b = Numnum(1.5)
c = 2.1 * a + 3 * b
d = -1.0 * a + 1.8 * b
e = c * d / 2.0
f = e**2
print(f'{f.data:.6f}') # This can mimic the forward pass, i.e. resulting in the loss value
f.backward()           # This can mimic the backward pass, i.e. calculating dependency of the loss value to all the parameters
print(f'{a.grad:.6f}') # prints 138.8338, i.e. the numerical value of dg/da
print(f'{b.grad:.6f}') # prints 645.5773, i.e. the numerical value of dg/db

```

# Testing

For testing purposes, we can use Pytorch as a reference to examine the results. For that we need to install Pytorch and run Pytest.

pip install pytorch
python -m pytest
