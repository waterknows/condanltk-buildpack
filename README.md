CondaNLTK Buildpack
===============

This is a [Heroku Buildpack](https://devcenter.heroku.com/articles/buildpacks) that enables and integrates the installation of binary packages through [Conda](http://conda.pydata.org/), [PIP](https://pip.pypa.io/en/stable/) and [NLTK Downloader](http://www.nltk.org/data.html). It is modified from this [Conda Buildpack](https://github.com/trib3/conda-buildpack.git).

The default environment is Python 3 with Miniconda3. 

### Installation
You can add it to an existing application. To avoid downloading duplicated packages, please do not use other python buildpacks concurrently.

```console
$ heroku buildpacks:set https://github.com/yuxiaosun/condanltk-buildpack.git -a [app-name]
```

### Usage
List the following files in your app's root directory:
* conda-requirements.txt: list packages installed by conda, split by new line.
* requirements.txt: list packages installed by pip, split by new line.
* nltk.txt: list data packages installed by nltk.downloader(), split by space. Don't forget to list "nltk" in conda-requirements.txt or "requirements.txt".
Refer to /text folder as an example.

### Tip
This buildpack will result in a large slug size upon first deployment to heroku app (~300MB). Subsequent builds will be much smaller (~200MB). You can also refer to this [article](https://robots.thoughtbot.com/how-to-reduce-a-large-heroku-compiled-slug-size) for reducing slug size. 


