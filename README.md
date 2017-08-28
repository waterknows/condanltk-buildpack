CondaNLTK Buildpack
===============

This is a [Heroku Buildpack](https://devcenter.heroku.com/articles/buildpacks) that enables and integrates the installation of binary packages through [Conda](http://conda.pydata.org/), [PIP](https://pip.pypa.io/en/stable/) and [NLTK Downloader](http://www.nltk.org/data.html).

The buildpack is built to install packages such as scikit-learn and NLTK Data that official buildpack cannot handle. The default environment is Python 3 with Miniconda3. 

### Installation
You can add it to an existing application using [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli). To avoid downloading duplicated packages, please do not use other python buildpacks concurrently.

```console
$ heroku buildpacks:add https://github.com/yuxiaosun/condanltk-buildpack.git -a [app-name]
$ git push heroku master
```

### Usage
Add the following text files in your app's root directory:
* conda-requirements.txt: list packages installed by conda, split by new line.
* requirements.txt: list packages installed by pip, split by new line.
* nltk.txt: list data packages installed by nltk.downloader(), split by space. Don't forget to list "nltk" in conda-requirements.txt or "requirements.txt".

The buildpack will download listed packages automatically. Refer to /text folder as an example usage.

### Tip
This buildpack will result in a large slug size upon first deployment to heroku app (~300MB). Subsequent builds will be much smaller (~200MB). You can also refer to this [article](https://robots.thoughtbot.com/how-to-reduce-a-large-heroku-compiled-slug-size) for reducing slug size. 

### Reference
* [Conda Buildpack](https://github.com/trib3/conda-buildpack.git).
* [Official Python Buildpack](https://github.com/heroku/heroku-buildpack-python)

