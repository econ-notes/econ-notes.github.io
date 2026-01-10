# 02. Frequently Used Environment-Related Conda Commands


## 1. Create an environment from a file 
```
conda env create -f env-data.yml
```

## 2. Update an environment
```
conda env update --file env-data.yml
```

## 3. Remove an environment
```
conda remove --name data --all
```

## 4. A basic environment for data-related tasks

```yml
name: data
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.13
  - pip
  - ipython
  - jupyter
  - numpy=2.3.4
  - sympy=1.14.0
  - scipy=1.15.3
  - pandas=2.3.3
  - pyarrow=22.0.0
  - polars=1.35.1
  - scikit-learn=1.7.2
  - statsmodels=0.14.5
  - linearmodels=7.0
  - patsy=1.0.2
  - matplotlib
  - seaborn
  - plotnine
  - shiny=1.4.0
  - pip:
    - pyfixest==0.40.1
    - FixedEffectModelPyHDFE==0.0.5
    - marginaleffects==0.2.2
```

---

> Author: Econ Notes  
> URL: http://localhost:1313/programming/python-notes/01-conda/02-useful-commands/  

