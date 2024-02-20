# Utility functions for ["Mathematical Statistics with a View Toward Machine Learning"](https://mml.johnmyersmath.com/stats-book/index.html), by John Myers

A Python package for all utility functions used in the book and programming assignments. To install, do the usual:

```
pip install math_stats_ml
```

All other materials are contained [here](https://github.com/jmyers7/stats-book-materials).

**Table of contents**:

1. Gradient descent utilities (`gd` submodule)
    * [Container class for output of algorithms (`GD_output`)](#container-class-for-output-of-algorithms-gd_output)
    * [Gradient descent (`GD`)](#gradient-descent-gd)
    * [Stochastic gradient descent (`SGD`)](#stochastic-gradient-descent-sgd)

## Gradient descent utilities (`gd`)

### Container class for output of algorithms (`GD_output`)

```python 
class GD_output
```

A class holding the outputs of both the gradient descent ([`GD`](#gradient-descent-gd)) and stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithms. All attributes below are optional and default to `None`.

#### Attributes

Name | Type | Description
| :- | :- | :- |
|`parameters`| `dict` | A dictionary containing the parameters of the objective function passed to either [`GD`](#gradient-descent-gd) or [`SGD`](#stochastic-gradient-descent-sgd). Each value in the dictionary is a tensor whose zero-th dimension indexes the number of gradient steps.
| `per_step_objectives` | `torch.Tensor` | A tensor containing the running objective values, per gradient step.
| `per_epoch_objectives` | `torch.Tensor`| A tensor containing the running mean objective values, per epoch.
| `epoch_step_nums` | `torch.Tensor` | A tensor containing the number of each gradient step on which an epoch begins/ends.
| `grad_steps` | `iter` | An iterable ranging from $0$ to one less than the total number of gradient steps. (This is convenient for plotting purposes.)
| `lr` | `float` | Learning rate.
| `num_steps` | `int` | Number of gradient steps to run the gradient descent ([`GD`](#gradient-descent-gd)) algorithm.
| `decay_rate` | `float` | Learning rate decay.
| `batch_size` | `int` |Mini-batch size for the stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithm.
| `num_epochs` | `int` | Number of epochs for the stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithm.
| `max_steps` | `int` | Maximum number of gradient steps after which we terminate the stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithm.
| `type_flag` | `str` | Either `None` or `gd`. In the latter case, indicates whether the `GD_output` object was obtained from the gradient descent ([`GD`](#gradient-descent-gd)) algorithm.

### Gradient descent (`GD`)

```python
GD(J, init_parameters, lr, num_steps, decay_rate=0)
```

Implementation of gradient descent. The notation below is intended to match the notation in the description in the book [here](https://mml.johnmyersmath.com/stats-book/chapters/11-optim.html#gd-alg).

#### Output

The output type is an object of the [`GD_output` class](#container-class-for-output-of-algorithms-gd_output).

#### Parameters

Name | Type | Description
| :- | :- | :- |
| `J` | function | Objective function to be minimized. The parameters of the function are either a single tensor or a dictionary of tensors (in the case that the parameters fall into natural groups, e.g., weights and biases).
| `init_parameters` | `torch.Tensor` or `dict` | Initial parameters.
| `lr` | `float` | Learning rate, corresponding to $\alpha$ in the book.
| `num_steps` | `int` | The number of gradient steps after which the algorithm should halt, corresponding to $N$ in the book.
| `decay_rate` | `float` | Learning rate decay, corresponding to $\beta$ in the book. Defaults to $0$.


### Stochastic gradient descent (`SGD`)

```python
SGD(g, init_parameters, X, lr, batch_size, num_epochs, y=None, decay_rate=0, max_steps=-1, shuffle=True, random_state=None)
```

Implementation of stochastic gradient descent. The notation below is intended to match the notation in the description in the book [here](https://mml.johnmyersmath.com/stats-book/chapters/11-optim.html#sgd-alg).

#### Output

The output type is an object of the [`GD_output` class](#container-class-for-output-of-algorithms-gd_output).

#### Parameters

Name | Type | Description
| :- | :- | :- |
| `g` | function | Component of the stochastic objective function to be minimized. (The notation is intended to match the notation in the book.) The call signature of the function is of the form `g(X, parameters)` or `g(X, y, parameters)`, where `X` and `y` are explained below, and `parameters` is either a single parameter tensor or a dictionary of parameter tensors.
| `init_parameters` | `torch.Tensor` or `dict` | Initial parameters.
| `X` | `torch.Tensor` | Design matrix holding the dataset in its rows.
| `lr` | `float` | Learning rate, corresponding to $\alpha$ in the book.
| `batch_size` | `int` | Mini-batch size, corresponding to $k$ in the book.
| `num_epochs` | `int` | The number of epochs after which the algorithm should halt, corresponding to $N$ in the book.
| `y` | `torch.Tensor` | Ground truth labels for the data in the design matrix `X`. Optional.
| `decay_rate` | `float` | Learning rate decay, corresponding to $\beta$ in the book. Defaults to $0$.
| `max_steps` | `int` | Maximum number of gradient steps after which the algorithm should halt. Defaults to $-1$, in which case the algorithm will complete all `num_epochs` many epochs.
| `shuffle` | `bool` | Determines whether to shuffle the dataset before looping through an epoch. Defaults to `True`.
| `random_state` | `int` | If not `None` and `shuffle=True`, random seed to be passed to `torch.manual_seed`. Defaults to `None`.