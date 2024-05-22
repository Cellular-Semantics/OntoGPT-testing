# Installation and Usage Guide for OntoGPT and LinkML

This document contains all the necessary steps to install and run OntoGPT, set up the necessary environment, and use LinkML schemas to manage data models effectively within OntoGPT. 


## Prerequisites

* Python 3.9+
* OpenAI API Key: Obtain your API key by following this [OpenAI API guide](https://platform.openai.com/docs/api-reference/introduction).



## Installing OntoGPT

To install OntoGPT, follow this [setup guide](https://github.com/monarch-initiative/ontogpt/blob/main/docs/setup.md). 

OntoGPT can be installed using one of the following methods:

### Install via pip

For a quick installation:
  
```pip install ontogpt```


   
### Install via GitHub (**Recommended**)

For a customisable setup with the latest updates:

**1) Clone OntoGPT GitHub repository:**

```git clone https://github.com/monarch-initiative/ontogpt.git```

```cd ontogpt/```

**2) Install Dependencies Using poetry:** 

```poetry install```

### Set Up Your OpenAI API Key

Once OntoGPT is installed, configure Your OpenAI API Key:

```runoak set-apikey -e openai <your_openai_api_key>```



## Running OntoGPT

To operate OntoGPT, Follow this [operation guide.](https://github.com/monarch-initiative/ontogpt/blob/main/docs/operation.md)

**1) Prepare Your Input File:**

Create a text file named **example.txt** containing the text for processesing.

**2) Run OntoGPT with the specified model:**

```ontogpt complete example.txt --model gpt-3.5-turbo```


## Creating and Using LinkML Schemas

### Creating a LinkML Schema

* **Define Your Schema:** Create a **filename.yaml** that describes your data model. For guidance on building custom schemas, follow this [custom schema guide.](https://monarch-initiative.github.io/ontogpt/custom/.)


### Generating Pydantic Models 

* Once your LinkML schema is defined, generate **python classes** using the LinkML gen-pydantic tool :

```gen-pydantic --pydantic-version 2 filename.yaml > filename.py```

* This generates a python file **filename.py** with Pydantic models necessary for OntoGPT to interact programmatically with the data defined in your schema. This python file is generated in the same folder that contains the yaml schema file.



## Installing Custom LinkML Schemas

To install custom LinkML schemas, follow this [custom installation guide.](https://monarch-initiative.github.io/ontogpt/custom/)

Once you have prepared the linkml schema and the corresponding python file, place these files in the correct directory:

### If OntoGPT is installed via pip:

**1) Find the OntoGPT Installation Directory (where the OntoGPT package has been installed in your python environment):**

``` pip show ontogpt ```

**2) Move Schema Files to the **Templates** Directory in that path where OntoGPT has been installed:**

``` mv filename.yaml filename.py /path/to/env/lib/python3.9/site-packages/ontogpt/templates/ ```

**3) Use the Schema with OntoGPT Tools:**

``` ontogpt extract -t filename -i input.txt ```

This tells OntoGPT to use your **filename.yaml** schema to extract knowledge/data from your input file **input.txt**

### If OntoGPT is installed directly from its GitHub repository:

**1) Place the schema files in ```src/ontogpt/templates``` directory of your local OntoGPT repository clone:**

```mv filename.yaml filename.py src/ontogpt/templates/```

**2) Ensure everything is intergated properly by running:**

```make```

**3) Use the Schema to Extract Data:**

``` ontogpt extract -t filename -i input.txt ```

This tells OntoGPT to use your **filename.yaml** schema to extract knowledge/data from your input file **input.txt**



## Resources 

* OntoGPT GitHub Repository: https://github.com/monarch-initiative/ontogpt
* LinkML Documentation: https://linkml.io/linkml/
* OpenAI API Documentation: https://platform.openai.com/docs/api-reference/introduction



```python

```
