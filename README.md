# Part of Jupyter Docker Scipy with Python SQL Driver

This image includes the packages that I use most of the [entire Jupyter scientific ecosystem](https://jupyter.org/) with the addition of the ODBC Driver for SQL Server (pyodbc)

The following components are included:

- Everything in [cjadeveloper/jupyter-minimal](https://cloud.docker.com/repository/docker/cjadeveloper/jupyter-minimal) and its ancestor images
- [pandas](https://pandas.pydata.org/), [numexpr](https://github.com/pydata/numexpr), [matplotlib](https://matplotlib.org/), [scipy](https://www.scipy.org/), [seaborn](https://seaborn.pydata.org/), [sympy](http://www.sympy.org/en/index.html), [cloudpickle](https://github.com/cloudpipe/cloudpickle), [dill](https://pypi.python.org/pypi/dill), [numba](https://numba.pydata.org/), [bokeh](https://docs.bokeh.org/en/latest/), [sqlalchemy](https://www.sqlalchemy.org/), [vincent](https://vincent.readthedocs.io/en/latest/index.html), [beautifulsoup](https://www.crummy.com/software/BeautifulSoup/), [protobuf](https://developers.google.com/protocol-buffers/docs/pythontutorial), and [xlrd](http://www.python-excel.org/) packages
- [ipywidgets](https://ipywidgets.readthedocs.io/en/stable/) for interactive visualizations in Python notebooks
- [pyodbc driver](https://docs.microsoft.com/en-us/sql/connect/python/pyodbc/python-sql-driver-pyodbc?view=sql-server-ver15) for SQL Server

## Several ways to use this image

**Example 1:** This command pulls the lasted `cjadeveloper/jupyter-scipy` from Docker Hub if it is not already present on the local host. It then starts a container running a Jupyter Notebook server and exposes the server on host port 8888. The server logs appear in the terminal. Visiting `http://<hostname>:8888/?token=<token>` in a browser loads the Jupyter Notebook dashboard page, where `hostname` is the name of the computer running docker and `token` is the secret token printed in the console. The container remains intact for restart after the notebook server exits.:

```bash
docker run -p 8888:8888 cjadeveloper/jupyter-scipy
```

**Example 2:** This command performs the same operations as **Example 1**, but it exposes the server on host port 10000 instead of port 8888 and assign the name `my_jupyter` to the container. Visiting `http://<hostname>:10000/?token=<token>` in a browser loads the Jupyter Notebook dashboard page, where `hostname` is the name of the computer running docker and `token` is the secret token printed in the console.

```bash
docker run -p 8888:8888 --name my_jupyter cjadeveloper/jupyter-scipy
```

**Example 3:** This command pulls the lasted `cjadeveloper/jupyter-scipy` image from Docker Hub if it is not already present on the local host. It then starts an *ephemeral* container running a Jupyter Notebook server and exposes the server on host port 8888. The command mounts the current working directory on the host as `/home/johndoe/work` in the container. The server logs appear in the terminal. Visiting `http://<hostname>:8888/?token=<token>` in a browser loads [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/), where `hostname` is the name of the computer running docker and `token` is the secret token printed in the console. Docker destroys the container after notebook server exit, but any files written to `~/work` in the container remain intact on the host.

### Linux/Mac Containers: Env vars with "$var"

```bash
docker run --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/johndoe/work cjadeveloper/jupyter-scipy
```

### Windows Container: Env vars with "%var%"

```console
docker run --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "%CD%":/home/johndoe/work cjadeveloper/jupyter-scipy
```

> Basado en [Docker Jupyter Stack](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)
