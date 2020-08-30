# Data Science

![img](https://www.houseofbots.com/images/news/11775/cover.png)

Data science is an interdisciplinary field about processes and systems to extract knowledge or insights from data in various forms, either structured or unstructured, which is a continuation of some of the data analysis fields.

Or in simpler words, by ‘Data Science’ we mean almost everything that has something to do with data: Collecting, analyzing, modeling…

It is a set of disciplines and practices that handle data in a scientific manner. Usually, it includes but not limited to these steps:

* **Data acquisition**
  
  Is the process of gathering, filtering, and cleaning data before the data is put in a data warehouse or any other storage solution. The data could be in the form of .CSV files. Excel file (.XLSX) is a typical form, or it could be available by API calls.

*  **Data cleaning & wrangling**
    
   Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect, incomplete, irrelevant, duplicated, or improperly formatted. This data is usually not necessary or helpful when it comes to analyzing data because it may hinder the process or provide inaccurate results. 

* **Data Engineering**
  
  The aspect of data science that focuses on practical applications of data collection and analysis. For all the work that data scientists do to answer questions using large sets of information, there have to be mechanisms for collecting and validating that information.



### Big data

Big Data is a term used to describe a collection of data that is huge in volume and yet growing exponentially with time. In short such data is so large and complex that none of the traditional data management tools are able to store it or process it efficiently. The importance of big data doesn’t revolve around how much data you have, but what you do with it. 

IT is a combination of structured, semistructured and unstructured data collected by organizations that can be mined for information and used in machine learning projects, predictive modeling and other advanced analytics applications.

Big data comes from different sources, such as business transaction systems, customer databases, medical records, internet clickstream logs, mobile applications, social networks, scientific research repositories, machine-generated data and real-time data sensors used in internet of things (IoT) environments.

BigData' could be found in three forms:

1. Structured:
   
   Any data that can be stored, accessed and processed in the form of fixed format is termed as a 'structured' data.

   Example: A simple excel sheet

2. Unstructured:
   
   Any data with unknown form or the structure is classified as unstructured data. In addition to the size being huge, un-structured data poses multiple challenges in terms of its processing for deriving value out of it. 

   Example: the rsualt of a google search

3. Semi-structured:
   
   Semi-structured data can contain both the forms of data. We can see semi-structured data as a structured in form but it is actually not defined with e.g. a table definition

   Example of semi-structured data is a data represented in an XML file.


### Business Intelligence And Analytics

Business intelligence and analytics are data management solutions implemented in companies and enterprises to collect historical and present data, while using statistics and software to analyze raw information, and deliver insights for making better future decisions.

**Business intelligence** – Deals with what happened in the past and how it happened leading up to the present moment. It identifies big trends and patterns without digging too much into the why’s or predicting the future.

**Business analytics** – Deals with the why’s of what happened in the past. It breaks down contributing factors and causality. It also uses these why’s to make predictions of what will happen in the future.

### Machine Learning

Machine learning is an application of artificial intelligence (AI) that provides systems the ability to automatically learn and improve from experience without being explicitly programmed. Machine learning focuses on the development of computer programs that can access data and use it learn for themselves.

The process of learning begins with observations or data, such as examples, direct experience, or instruction, in order to look for patterns in data and make better decisions in the future based on the examples that we provide. The primary aim is to allow the computers learn automatically without human intervention or assistance and adjust actions accordingly.

Machine learning algorithms are often categorized as supervised or unsupervised.

Supervised machine learning algorithms can apply what has been learned in the past to new data using labeled examples to predict future events.The system is able to provide targets for any new input after sufficient training. The learning algorithm can also compare its output with the correct, intended output and find errors in order to modify the model accordingly.

In contrast, unsupervised machine learning algorithms are used when the information used to train is neither classified nor labeled. Unsupervised learning studies how systems can infer a function to describe a hidden structure from unlabeled data. The system doesn’t figure out the right output, but it explores the data and can draw inferences from datasets to describe hidden structures from unlabeled data.

### Deep Learning

Deep learning is an artificial intelligence (AI) function that imitates the workings of the human brain in processing data and creating patterns for use in decision making. Deep learning is a subset of machine learning in artificial intelligence that has networks capable of learning unsupervised from data that is unstructured or unlabeled. Also known as deep neural learning or deep neural network.

Deep learning is a machine learning technique that teaches computers to do what comes naturally to humans: learn by example. Deep learning is a key technology behind driverless cars, enabling them to recognize a stop sign, or to distinguish a pedestrian from a lamppost. It is the key to voice control in consumer devices like phones, tablets, TVs, and hands-free speakers.

In deep learning, a computer model learns to perform classification tasks directly from images, text, or sound. Deep learning models can achieve state-of-the-art accuracy, sometimes exceeding human-level performance. Models are trained by using a large set of labeled data and neural network architectures that contain many layers.


# JupyterLab

The Project Jupyter (formally known as IPython) is a polyglot, web-based, open-source data science tool. Fostering reuse and reproducibility, it supports interactive data science and scientific computing across multiple programming languages (the so-called kernels) via the idea of notebooks.

The language-agnostic behavior of Jupyter has made it a possible game-changer, as it unites multiple open source communities around the same tool. It now has a large community and is growing insanely fast, resulting in numerous extensions popping up at Github


# NumPy 

NumPy is a python library used for working with arrays. It also has functions for working in domain of linear algebra, fourier transform, and matrices.

Numpy is a general-purpose array-processing package. It provides a high-performance multidimensional array object, and tools for working with these arrays. It is the fundamental package for scientific computing with Python.


Array in Numpy is a table of elements (usually numbers), all of the same type, indexed by a tuple of positive integers. In Numpy, number of dimensions of the array is called rank of the array.A tuple of integers giving the size of the array along each dimension is known as shape of the array. An array class in Numpy is called as ndarray. Elements in Numpy arrays are accessed by using square brackets and can be initialized by using nested Python Lists.


#### Creating a Numpy Array

Arrays in Numpy can be created by multiple ways, with various number of Ranks, defining the size of the Array. Arrays can also be created with the use of various data types such as lists, tuples, etc. The type of the resultant array is deduced from the type of the elements in the sequences.

    
    import numpy as np
    
    
    arr = np.array([1, 2, 3])
    print(arr)
    
    
    # Creating an array from tuple
    arr = np.array((1, 3, 2))
    print("\nArray created using "
        "passed tuple:\n", arr)


Output:

    
    [1 2 3]
    
    Array created using passed tuple:
    [1 3 2]






