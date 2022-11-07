## Install Python
`brew install python`

## Call out pip installation for Python
`python3.10 -m pip`

## Install pip
If script is not available,supply curl command to download file and execute it.
`python get-pip.py`
This will install pip for the provided python.

If python links to => 3.7
pip will be installed for 3.7, and all the dependecy will go for 3.7

If python link to python3, get-pip.py will install pip3
If python link to python2, get-pip.py will install pip2

The dependecies are generally stored in site package in `/Library/Python`

Download the get-pip.py <br/>
`$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py` <br/>
`$ python3 get-pip.py` <br/>

## Upgrading pip
`$ pip install --upgrade pip`


## Find out pip2 version & Update
`which pip2` </br>
`sudo -H pip2 install --upgrade pip`

## Find out pip3 version & Update
`which pip3` </br>
`sudo -H pip3 install --upgrade pip`

## Uninstall pip
`sudo -H pip3 uninstall pip`

## Install a package via pip | skip cache directory
`pip install matplotlib --no-cache-dir`

## JupyterLab notebook or jupyter lab can be installed using conda or pip.
`pip install notebook`
<br/>`pip install jupyterlab`

## To run the jupyter notebook or jupyter lab, run the following command at the Terminal
`jupyter notebook`
<br/>`jupyter lab`

## Creating a Virtual Environment
Install `virtualenv` using `sudo` if not already present

`$ sudo pip install virtualenv`

`$ virtualenv -p python3.8 audioenv`

### Create Envitonment
`$ python3 -m venv virtual`

### Activate Envitonment
`$ source virtual/bin/activate`

## Find out which Python version pip points to
$ `pip -V`


### Import External JAR in notebook
```python
from pyspark.sql.session import SparkSession
from pyspark import SparkContext


spark = SparkSession \
    .builder \
    .appName("GraphFrames Analytics") \
    .getOrCreate()


sc = spark.sparkContext
sc.addPyFile('/Users/amar/graphframes-0.5.0-spark2.1-s_2.11.jar')

from graphframes import GraphFrame
```

