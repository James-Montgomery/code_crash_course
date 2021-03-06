# Conda Virtual Environments

Conda is a python specific virtual environment manager that comes with the Anaconda distribution of python.

## Installation

Simply follow the Andaconda installation instructions in the [python section](../../Python/README.md).

## Use

First, let's define the fundamentals of our environment:

~~~Bash
conda create --name python_env python=3.6.3
~~~

Here we have created a virtual environment named `python_env` with python 3.6.3 installed. If we wanted to use the Anaconda distribution of python specifically, we could add `anaconda` as an additional argument at the end.

When the environment is finished building, we can activate it quite simply:

~~~Bash
conda activate python_env
~~~

Now let's install some stuff! For example, jupyter notebooks for code development. We could use the normal python installation methods:

~~~Bash
pip install --user ipykernel
# or
conda install ipykernel
~~~

Or you can install from the requirements list provided in this directory.

~~~Bash
pip install -r requirements.txt
~~~

If we want jupyter to recognize our environment as a valid kernel, we will need to add the environment:

~~~Bash
python -m ipykernel install --user --name=python_env
~~~

As long as the environment is active you can use it just as you would the default environment. If you want to put away the environment for later use, simply deactivate it.

~~~Bash
conda deactivate
~~~

Before deactivating you might want to save your dependancies for reference. Simply save then to a requirements file.

~~~Bash
pip freeze > requirements.txt
~~~

## Clean Up

If you no longer need an environment, simply delete it:

~~~Bash
conda remove -n python_env -all
~~~

You can also remove the jupyter kernel associated with it:

~~~Bash
jupyter kernelspec list
jupyter kernelspec uninstall python_env
~~~

If you ever want to see a list of your available conda environments:

```
conda env list
```

# Conda for Julia

You can also create conda virtual environments for Julia!

```
conda create -n julia_env -c conda-forge julia
```

Julia does not have a nice package manager like pip (as of the writing of this document). You can opt to use `.toml` files to manage project dependancies, but I find these files tedious. Instead, I prefer to use `requirement.jl` files. These must be written manually, but work well in practice when developing proof of concept work.

```
julia requirements.jl
```

# Conda for R

```
conda create -n r_env r-essentials r-base
```

```
julia requirements.R
```
