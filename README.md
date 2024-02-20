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

```python 
class GD_output
```

A class holding the outputs of both the gradient descent ([`GD`](#gradient-descent-gd)) and stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) functions. All attributes below are optional and default to `None`.

*Attributes*:

`parameters`: `dict`

A dictionary containing the parameters of the objective function passed to either [`GD`](#gradient-descent-gd) or [`SGD`](#stochastic-gradient-descent-sgd).

`per_step_objectives`: `torch.Tensor`

A tensor containing the running objective values, per gradient step.

`per_epoch_objectives`: `torch.Tensor`

A tensor containing the running mean objective values, per epoch.

`epoch_step_nums`: `torch.Tensor`

A tensor containing the number of each gradient step on which an epoch begins/ends.

`grad_steps`: `iter`

An iterable ranging from $0$ to one less than the total number of gradient steps. (This is convenient for plotting purposes.)

`lr`: `float`

Learning rate.

`num_steps`: `int`

Number of gradient steps to run the gradient descent ([`GD`](#gradient-descent-gd)) algorithm.

`decay_rate`: `float`

Learning rate decay.

`batch_size`: `int`

Mini-batch size for the stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithm.

`num_epochs`: `int`

Number of epochs for the stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithm.

`max_steps`: `int`

Maximum number of gradient steps after which we terminate the stochastic gradient descent ([`SGD`](#stochastic-gradient-descent-sgd)) algorithm.

`type_flag`: `str`

Either `None` or `gd`. In the latter case, indicates whether the `GD_output` object was obtained from the gradient descent ([`GD`](#gradient-descent-gd)) algorithm.

### Container class for output of algorithms (`GD_output`)

### Gradient descent (`GD`)

### Stochastic gradient descent (`SGD`)