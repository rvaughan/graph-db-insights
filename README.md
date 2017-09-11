# Get insights from OrientDB graph database in IBM Data Science Experience.

Graph databases are well-suited for analyzing interconnections, which is why there has been a lot of interest in using graph databases to mine data from social media. Graph databases are also useful for working with data in business disciplines that involve complex relationships and dynamic schema, such as supply chain management, identifying the source of an IP telephony issue and creating "customers who bought this also looked at..." recommendations.

This tutorial gives you a head start on how to work with OrientDB database on IBM Data Science Experience(DSX) using pyorient.This journey will help developers get started with various orientdb operations like CRUD, basic traversal and extracting insights using python driver for orientDB- `pyorient`.

In this journey we will demonstrate:
* Setting up ipython notebook on DSX connecting to orientdb using pyorient.
* Hands-on on the crud operations and extracting insights from graph database

![](doc/source/images/architecture.png)

1. The Kuberntes Cluster on which orientdb is running.
2. Orientdb instance on kubernetes.
3. Object storage stores the config file and kaggle imdb data.
4  Config file and data used in the jupyter notebook.
5. The Jupyter notebook processes the data and generates insights.It can viewed in orientdb Studio.
6. The Jypyter notebook is powered by Spark.
 

   
## Included components

* [Orientdb](http://orientdb.com/orientdb/): A Multi-Model Open Source NoSQL DBMS.

* [IBM Data Science Experience](https://apsportal.ibm.com/analytics): Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark.

* [Bluemix Object Storage](https://console.ng.bluemix.net/catalog/services/object-storage/?cm_sp=dw-bluemix-_-code-_-devcenter): A Bluemix service that provides an unstructured cloud data store to build and deliver cost effective apps and services with high reliability and fast speed to market.

* [Jupyter Notebooks](http://jupyter.org/): An open-source web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.

* [Kubernetes Clusters](https://console.ng.bluemix.net/docs/containers/cs_ov.html#cs_ov)

* [Bluemix container service](https://console.ng.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers)

## Featured technologies

* [Data Science](https://medium.com/ibm-data-science-experience/): Systems and scientific methods to analyze structured and unstructured data in order to extract knowledge and insights.

## Prerequisite

Create a Kubernetes cluster with [IBM Bluemix Container Service](https://github.com/IBM/container-journey-template) to deploy in cloud.Deploy orientdb on kubernetes container using [Deploy Orientdb on container]( https://github.com/IBM/deploy-graph-db-container). 

# Watch the Video
Watch this video to get an overview of this developer Journey.(Video yet to be made.)


# Steps

Follow these steps to setup and run this developer journey. The steps are
described in detail below.


1. [Get started with orientdb on Data Science Experience using PyOrient](#1-get-started-with-orientdb-on-data-science-experience-using-pyorient)
1. [Sign up for the Data Science Experience](#2-sign-up-for-the-data-science-experience)
1. [Create the notebook](#3-create-the-notebook)
1. [Add the data](#4-add-the-data)
1. [Update the notebook with service credentials](#5-update-the-notebook-with-service-credentials)
1. [Run the notebook](#6-run-the-notebook)


## 1. Get started with orientdb on Data Science Experience using PyOrient.
PyOrient is a python driver for orientdb.If you are using the Data Science Experience ( DSX) , Setting up the orientdb on kubernetes is important.This is because if you set up the orientdb locally, you won’t able to access it through DSX, as the orientdb console port 2424 and orientdb studio 2480 wouldn’t be exposed on bluemix.Deploy orientdb on kubernetes container using [Deploy Orientdb on Kubernetes]( https://github.com/IBM/deploy-graph-db-container) will expose the ports on bluemix through which orientdb can be accessed from the notebook on data science experience.You can use the ip-address of your cluster and node port on which the port 2424 orientdb console is mapped, to access that orientdb through notebook.However, you can always run the notebook and orientdb on your local system.

Set up the Notebook on Data Science experience with object storage using following steps :

## 2. Sign up for the Data Science Experience

Sign up for IBM's [Data Science Experience](http://datascience.ibm.com/). By signing up for the Data Science Experience, two services: ``DSX-Spark`` and ``DSX-ObjectStore`` will be created in your Bluemix account.

## 3. Create the notebook

* Open [IBM Data Science Experience](https://apsportal.ibm.com/analytics). 
* Use the menu on the top to select `Projects` and then `Default Project`.
* Click on `Add notebooks` (upper right) to create a notebook.
* Select the `From URL` tab.
* Enter a name for the notebook.
* Optionally, enter a description for the notebook.
* Enter this Notebook URL: https://github.com/IBM/graph-db-insights/blob/master/notebooks/graphdb-insights.ipynb
* Click the `Create Notebook` button.

## 4. Add the data 

##### Add the data to the notebook
* Please download the files from :
 https://www.kaggle.com/deepmatrix/imdb-5000-movie-dataset .
* Trim the data to 600 rows for the purpose of this tutorial and Rename the file  `Graphdb-Insights.csv`
* From your project page in DSX, click `Find and Add Data` (look for the `10/01` icon)
and its `Files` tab. 
* Click `browse` and navigate to `Graphdb-Insights.csv` on your computer.
* Add the files to Object storage.
* Repeat the above Steps for `config.json` as well.

![](doc/source/images/add_file.png)

## 5. Update the notebook with service credentials.

##### Add the Object Storage credentials to the notebook
* Select the cell below `3. Add your service credentials for Object Storage` section in the notebook to update the credentials for Object Store. 
* Use `Find and Add Data` (look for the `10/01` icon) and its `Files` tab. You should see the file names uploaded earlier. Make sure your active cell is the empty one created earlier. 
*  Select `Insert to code` below config.json and click insert credentials from the dropdown.
* Select `Insert to code` below Graphdb-Insights.csv(movie dataset) and click Insert Pandas Dataframe from the dropdown in the next cell.

## 6. Run the notebook

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.
* At a scheduled time.
  * Press the `Schedule` button located in the top right section of your notebook
    panel. Here you can schedule your notebook to be executed once at some future
    time, or repeatedly at your specified interval.

For this Notebook, To run every cell one by one is recommended.




