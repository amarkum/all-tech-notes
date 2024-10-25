
# Python and pip Installation Guide

This guide covers the steps for installing Python, managing `pip`, setting up virtual environments, and working with Jupyter notebooks.

---

## 1. Install Python

On macOS, Python can be installed using Homebrew:

```bash
brew install python
```

---

## 2. pip Installation and Management

### Call Out pip Installation for a Specific Python Version
If a specific Python version is needed, `pip` can be called out as follows:

```bash
python3.10 -m pip
```

### Install pip (if not already installed)
To install `pip` for Python, use `get-pip.py`.

1. **Download the `get-pip.py` file**:
   ```bash
   curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
   ```

2. **Run the Installation Script**:
   ```bash
   python3 get-pip.py
   ```

- If `python` links to `python3`, `get-pip.py` will install `pip3`.
- If `python` links to `python2`, `get-pip.py` will install `pip2`.

### Dependency Storage

Dependencies installed by `pip` are stored in the `site-packages` directory. Common path on macOS:
```plaintext
/Library/Python
```

---

## 3. Upgrading pip

Upgrade `pip` to the latest version:
```bash
pip install --upgrade pip
```

### Find and Update pip2 and pip3 Versions

1. **Check `pip2` version and update**:
   ```bash
   which pip2
   sudo -H pip2 install --upgrade pip
   ```

2. **Check `pip3` version and update**:
   ```bash
   which pip3
   sudo -H pip3 install --upgrade pip
   ```

### Uninstall pip
To remove `pip3`:
```bash
sudo -H pip3 uninstall pip
```

---

## 4. Installing Packages via pip

To install a package without caching:
```bash
pip install matplotlib --no-cache-dir
```

---

## 5. Jupyter Notebook and JupyterLab Installation

Jupyter can be installed using `pip`:

```bash
pip install notebook
pip install jupyterlab
```

### Launch Jupyter Notebook or JupyterLab
Run the following command in the terminal:

```bash
jupyter notebook
jupyter lab
```

---

## 6. Creating a Virtual Environment

A virtual environment is an isolated Python environment for managing dependencies.

### Install `virtualenv` (if not already installed)
```bash
sudo pip install virtualenv
```

### Create a Virtual Environment
- Using `virtualenv` with a specific Python version:
  ```bash
  virtualenv -p python3.8 audioenv
  ```

- Using `venv`:
  ```bash
  python3 -m venv virtual
  ```

### Activate the Virtual Environment
Activate the virtual environment to work within it.

```bash
source virtual/bin/activate
```

### Check Python Version Associated with pip
Find out which Python version `pip` points to:
```bash
pip -V
```

---

## 7. Importing External JARs in Jupyter Notebooks

In a Jupyter notebook, you can import external JAR files with `pyspark`:

```python
from pyspark.sql.session import SparkSession
from pyspark import SparkContext

# Initialize Spark session
spark = SparkSession.builder.appName("GraphFrames Analytics").getOrCreate()

# Add JAR file to Spark context
sc = spark.sparkContext
sc.addPyFile('/Users/amar/graphframes-0.5.0-spark2.1-s_2.11.jar')

from graphframes import GraphFrame
```

---

This guide provides a comprehensive approach to installing Python, managing `pip`, setting up virtual environments, and working with Jupyter notebooks and external libraries.
