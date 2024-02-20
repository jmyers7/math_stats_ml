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

`objectives`: `torch.Tensor`

`per_step_objectives`: `torch.Tensor`

`per_epoch_objectives`: `torch.Tensor`

`epoch_step_nums`: `torch.Tensor`

`grad_steps`: `iter`

`lr`: `float`

`num_steps`: `int`

`decay_rate`: `float`

`batch_size`: `int`

`num_epochs`: `int`

`max_steps`: `int`

`type_flag`: `str`

### Container class for output of algorithms (`GD_output`)

### Gradient descent (`GD`)

### Stochastic gradient descent (`SGD`)