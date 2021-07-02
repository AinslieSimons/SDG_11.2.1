# Project: Analysis_SDG_11.2.1

This is project to build a data pipeline to analyse data for the UN Sustainable Development Goal indicator 11.2.1, which is part of goal 11 which has the aim to:

> "Make cities and human settlements inclusive, safe, resilient and sustainable"
# Method

By assessing geocoded census data and geocoded public transport access points (stops and stations), an assessment can be made about the degree of accessibility individuals in the population have to public transport.

# Accessibility

A stop or station is considered 'accessible' if it is within 500 metres of a person's place of living. That distance is the one given by official methodology. We recognise this is a problematic and arbitrary figure. How accessible a public transport access point to an individual will depend on many factor such as:

- the individual’s physical abilities
- certain disabilities
- gradient
- path quality
- obstacles (e.g. a fence in the way of an otherwise close access point)

## Aims of the project

The aims are:

* to build a data pipeline that can analyse data to assess the availability of public transport services for the population of the UK
* to make the code reusable so that it may be able to analyse other data and:
    * assess the availability of other services across the UK
    * be used to assess the availability of services in other nations

# The team

The coding of this project has been carried out primarily by staff at the Office for National Statistics. The primary programmer and project lead is James Westwood. Geospatial advice has been given Musa Chirikeni. Planning help, advice and support was provided by Lucy Gwilliam. And assistance with the planning of the original method and code was provided by Michael Hodge.

## Process

![step1](https://github.com/james-westwood/SDG_11.2.1/raw/master/img_readme/11-2-1-process-step1.jpg)

![step2](https://github.com/james-westwood/SDG_11.2.1/raw/master/img_readme/11-2-1-process-step2.jpg)

![step3](https://github.com/james-westwood/SDG_11.2.1/raw/master/img_readme/11-2-1-process-step3.jpg)


## Deliverables of the project

1. Open source reuseable code which relies only on open source resources
2. A new dataset with analysis of public transport availability for the UK population
3. Three additional datasets with analysis of public transport availability disagregated by sex, age and disabilities

## Next steps in development

- isolate the smallest areas available on the census dataset
- use the same method of creating a centroid and then a 5km buffer around those areas
- for every area, run a points in polygons enquiry to answer 'how many stops in the buffer?'
- generate a small dataset with columns `['area_name','population','stops_within_5km']
- create statistical pipeline for analysis

## Resources

- https://www.efgs.info/wp-content/uploads/2019/11/5a3_HugoPoelman.pdf

# Running the script

## Requirements:

A number of problems with dependencies have been experienced while developing this, so it is strongly recommended that you use a virtual environment (either conda or venv) and use the provided requirements.txt to install the needed versions of packages.


### Create an environment

I strongly recommend using an environment to minimise dependeny issues and avoid 'polluting' your main/base Python environment. Throughout this project mini conda has been used to install dependencies and create environments.

Here creating an environment called "SDG_11.2.1" with the version of Python that this was developed in

    conda create --name SDG_11.2.1 python=3.8

### Activate the environment

First go to the project directory

    $ cd project-directory

So in my case, the project directory was also called "SDG_11.2.1" (the same as the environment.)

Then activate the environment

    $ conda activate SDG_11.2.1

Or on Windows this would be

   $ activate SDG_11.2.1

Then you should see the environment name in brackets before the prompt, similar to:

    (SDG_11.2.1) $

As a quick check to see if the environment is activated, it might be wise to make sure you are using the correct Python interpreter by checking your Python path:

In Linux:

    $ which python

And in Windows use the following command in cmd or Anaconda prompt:

    $ where python

Which should return something like:

C:\Python36\envs\SDG_11.2.1\python.exe

Showing your are using the Python from the virtual environment, not the base installation of Python.

### Install the dependencies


You should be in correct directory, where [`requirements.txt`](_build\html\_sources\requirements.txt) exists. Run:

    (SDG_11.2.1) $ pip install -r requirements.txt


Note: On on Linux Ubuntu/Mint 18.04 you may have to install rtree from apt instead of pip. Run:

    (SDG_11.2.1) $ sudo apt install python3-rtree
