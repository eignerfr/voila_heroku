

## How to build and deploy voila apps via heroku

(partly based on these [instructions](https://github.com/martinRenou/voila_heroku))

1. First, create an Heroku account. There is a free account option that allows you to create up to 5 dyno containers.
2. Install Heroku on your machine following [these instructions](https://devcenter.heroku.com/articles/getting-started-with-python#set-up).
3. For each notebook based app (or folder of notebook based apps) you want to create clone this repository, or create your own repository that follows the same structure (one can use a different name obviously):

```bash
git clone https://github.com/jhconning/voila_heroku
```

3. Create your widget based jupyter notebook and put it in the `notebooks` directory
4. Add the dependencies needed for running your Notebook in the [requirements.txt](requirements.txt) file (see below for how to include any own user-created modules)
5. Edit the `Procfile` file and list the notebook to be processed, e.g.  `notebooks/bqplot.ipynb` 
6. Commit everything

```bash
git commit -m "My cool app on Heroku!"
```

8. Create the Heroku app:

```bash
heroku create
```

9. Now deploy your code:

```bash
git push heroku master
```

10. That's it! Now you can open your app using:

```bash
heroku open
```

This last command is just a shortcut for opening your browser to the right url where the app will be.  (By default heroku assigns some random URL name like  `https://calm-everglades-05991.herokuapp.com/`)

##Deploy with Heroku

This is based on Martin Renou's instructions.

0. Get a heroku account, install on windows. 

1. Create your Notebook and put it in the `notebooks` directory
2. Add the dependencies needed for running your Notebook in the `requirements.txt` file.
3. Edit the `Procfile` file by replacing `notebooks/bqplot.ipynb` by the path to your awesome Notebook
4. Commit everything

```
git commit -m "My awesome app on Heroku!"
```

1. Create the Heroku app:

```
heroku create
```

1. Now deploy your code:

```
git push heroku master
```

1. That's it! Easy right? Now you can open your app using:

```
heroku open
```



---

### Further notes

#### Creating user modules that are pip installable from github

If you want to install a user module such as `renegotiation.py` (which I wrote for Basu-Conning paper) one solution is to pip install from github.  So we'd add the following to the requirements.txt file:

```python
git+git://github.com/jhconning/renegotiation.git#egg=renegotiation
```

This requires that the repo has a properly configured `setup.py` (see e.g. [here](https://github.com/maet3608/minimal-setup-py)). 

Incidentally this also means one can pip install the module like this (here using the `Contract.py` file in the jhconning/renegotiation repo:

```
pip install git+https://github.com/jhconning/renegotiation.git#egg=Contract
```

