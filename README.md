---
title: "Fine-tuned Microsoft Phi-1.5 for Summarization"
author: "Sachin Kafle"
date: "3/23/2025"
output: html_document
---



# Overview
This document provides details on the fine-tuned **Microsoft Phi-1.5** model for summarization using **Salesforce's DialogStudio** dataset.

## Installation
Install the required dependencies before running the model:

```{r, eval=FALSE}
install.packages("reticulate")
library(reticulate)
py_install(c("torch", "transformers", "datasets", "evaluate"))
```

## Load Dataset
The model is trained on the **Salesforce DialogStudio** dataset. To load and preprocess the dataset:

```{python, eval=FALSE}
from datasets import load_dataset

dataset = load_dataset("Salesforce/DialogStudio")
dataset = dataset.map(lambda x: {"input_text": x["dialog"], "summary": x["summary"]})
```

## Fine-tuning the Model
Fine-tuning is performed using the **Hugging Face Transformers** library:
