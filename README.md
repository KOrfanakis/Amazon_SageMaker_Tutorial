# Building, Training, and Deploying a Machine Learning Model with Amazon SageMaker – A Short Tutorial

<br>

<div align="center">
  <img align="middle" src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" width="200" title="hover text">
  <img align="middle" src="https://camo.githubusercontent.com/5bd5379d5016983637fb8e1cb4a19287ca9103c32dd7687069b7fad6a5455a98/68747470733a2f2f7062732e7477696d672e636f6d2f6d656469612f4464522d6d6d47564141417a4747412e6a70673a6c61726765" width="400" title="hover text">
</div>

<br>

**Table of Contents:**

<!--ts-->
* [Motivation](#-motivation)
* [Introduction to Amazon SageMaker](#-introduction-to-amazon-sagemaker)
  * [What is it?](#what-is-it)
  * [Why use it?](#why-use-it)
* [Business Objective](#-business-objective)
* [Data](#-data)
* [Setup](#-setup)
* [References](#-references)
* [Feedback](#-feedback)
<!--te-->

<br>

## 🎯 Motivation

The aim of this mini-project is to teach how to use Amazon SageMaker to build, train, and deploy a Machine Learning (ML) model using the XGBoost algorithm. Specifically, we will develop a model that predicts whether a customer will subscribe to a product (bank term deposit) offered by a bank.

The code is adapted, with minor changes, from the hands-on tutorial '***[Build, train, and deploy a machine learning model with Amazon SageMaker](https://aws.amazon.com/getting-started/hands-on/build-train-deploy-machine-learning-model-sagemaker/?trk=el_a134p000003yWILAA2&trkCampaign=DS_SageMaker_Tutorial&sc_channel=el&sc_campaign=Data_Scientist_Hands-on_Tutorial&sc_outcome=Product_Marketing&sc_geo=mult&p=gsrc&c=lp_ds)***' provided by AWS. I have also reorganised the code to improve readability and added text in each section to make this tutorial easier to follow. Note that this is a short tutorial on using SageMaker; many aspects of the typical ML pipeline are not implemented.  

<br>

## 📚 Introduction to Amazon SageMaker

### What is it?

[Amazon SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html) is a fully managed AWS cloud service for data science and ML workflows. With SageMaker, data scientists and developers can quickly and easily build and train ML models and directly deploy them into a production-ready hosted environment.

SageMaker provides an integrated Jupyter authoring notebook instance for easy access to data sources for exploration and analysis so that the user doesn’t have to manage servers. It also provides common ML algorithms optimised to run efficiently against extremely large data in a distributed environment. With native support for bring-your-own-algorithms and frameworks, SageMaker offers flexible distributed training options that adjust to the user’s specific workflows and needs.

<br>

<div align="center">
  <img align="middle" src="https://www.zdnet.com/a/img/resize/0070de9aa1eee5d5be9a57f5b2771430f2e4157a/2020/12/21/ec9f1822-66c2-4f35-b0e7-59ca1955e6c8/amazon-aws-sagemaker-workflow.png?auto=webp&width=1092" width="700" title="hover text">
</div>

<br>

### Why use it?

There are several benefits to using cloud services such as SageMaker for data science and machine/deep learning (ML/DL) tasks. Firstly, cloud computing offers increased speed, scalability, and flexibility when it comes to computing needs:

- **Speed**: By leveraging technologies such as clusters of GPUs and CPUs to perform complex operations on compute-intensive tasks, users can design, develop and train ML/DL applications faster.
- **Scalability**: With the wide range of on-demand resources available through the cloud, users can deploy virtually unlimited resources to tackle complex tasks of any size.
- **Flexibility**: Several Deep learning frameworks (such as TensorFlow, Torch, Keras etc.) can be run on the cloud, allowing users to use packaged libraries of deep learning algorithms best suited for a particular use case, whether it’s for web, mobile or connected devices.

Additionally, the cloud makes ML/DL more accessible. SageMaker, in particular, enables more people and businesses to innovate with ML through a wide variety of tools, such as integrated development environments for data scientists and no-code visual interfaces for business analysts.

Finally, the cloud’s pay-as-you-go model means that users typically pay only for cloud services they use. This approach helps businesses lower operating costs, run their infrastructure more efficiently, and scale as the business needs change.

For more information, please refer to the following articles:

[1]	[What Is Amazon SageMaker?](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html) <br>
[2]	[Amazon SageMaker](https://aws.amazon.com/sagemaker/) <br>
[3]	[Deep Learning on AWS](https://aws.amazon.com/deep-learning/) <br>

<br>

## 💼 Business Objective

In an imaginary scenario, we are hired as data scientists by a banking institution that has compiled a dataset related to their marketing campaign. The dataset contains information on customer demographics, previous responses to marketing events, and external factors (see section [Data](#-data)).

The data also contains a target variable which identifies whether a previous customer is enrolled for a product offered by the bank. Our task is to develop an ML model that predicts whether a new customer will enrol based on their individual information and other external factors included in the dataset. The bank aims to use our data to target customers less likely to subscribe and offer them special deals and services.

<br>

## 📊 Data

The model will be trained on the [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/bank+marketing) that contains information on customer demographics, previous responses to marketing events, and external factors (such as employment variation rate and consumer confidence index). The data is related to direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact with the same client was required to access if the product (bank term deposit) would be (‘yes’) or not (‘no’) subscribed.

The data has been labelled for our convenience. The column ‘y_yes’ is our target variable as it identifies whether a customer is enrolled for a product offered by the bank. It is a binary feature (1 for ‘yes’, 0 for ‘no’), making this a binary classification task.

The original version of this dataset is publicly available from the [Machine Learning Repository](https://archive.ics.uci.edu/ml/index.php) curated by the University of California, Irvine.

<br>

## 🛠 Setup

The quickest setup to run the notebook requires:
- An AWS account
- Proper IAM User and Role setup
- An Amazon SageMaker Notebook Instance
- An S3 bucket (created when running the code in the Jupyter notebook)

To run the notebook, you need to get set up with a SageMaker notebook environment and clone in this repository. For instructions, please visit [this link](https://catalog.us-east-1.prod.workshops.aws/workshops/0c6b8a23-b837-4e0f-b2e2-4a3ffd7d645b/en-US/getting-started/setup) that demonstrates how to run code wither in an AWS hosted event or with your own AWS account.

<br>

## 📕 References

The principal resource for this mini-project is the hands-on tutorial '***[Build, train, and deploy a machine learning model with Amazon SageMaker](https://aws.amazon.com/getting-started/hands-on/build-train-deploy-machine-learning-model-sagemaker/?trk=el_a134p000003yWILAA2&trkCampaign=DS_SageMaker_Tutorial&sc_channel=el&sc_campaign=Data_Scientist_Hands-on_Tutorial&sc_outcome=Product_Marketing&sc_geo=mult&p=gsrc&c=lp_ds)***' provided by AWS.

Other resources include:

[1] [Cloud computing with AWS](https://aws.amazon.com/what-is-aws/) <br>
[2] [What Is Amazon SageMaker?](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html) and references therein <br>
[3] [Get Started with Amazon SageMaker Notebook Instances](https://docs.aws.amazon.com/sagemaker/latest/dg/gs-console.html) and references therein (specifically, the seven steps below that **Topics** section)

<br>

## 📞 Feedback

If you have any feedback or ideas to improve this project, feel free to contact me via:

<a href="https://twitter.com/korfanakis">
  <img align="left" alt="Twitter" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/twitter.svg" />
</a>

<a href="https://uk.linkedin.com/in/korfanakis">
  <img align="left" alt="LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />
</a>
