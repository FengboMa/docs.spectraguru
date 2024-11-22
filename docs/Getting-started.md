---
layout: default
title: Getting started
nav_order: 3
---

# Getting started
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Quick start

### Visit our site

{: .note }
As of August 16, 2024: For UGA internal use on the development branch. Please connect to the school's local area network (LAN), such as the school Wi-Fi PAWS-Secure, and visit [here](http://172.19.194.69:8501)!

Our application is hosted at [spectraguru.org](https://spectraguru.org)! It's straightforward to use — just follow the link and start exploring.


### Deploy locally

You do not need to host the application locally to use it. However, if you wish to deploy it on your local machine, please follow these steps:

- **Install Python and Dependencies**
   
   SpectraGuru requires the following packages:

       altair==5.3.0

       deprecation==2.1.0

       matplotlib==3.8.4

       numpy==1.23.5

       pandas==2.2.2

       scikit_learn==1.5.1

       scipy==1.14.0

       streamlit==1.35.0

       streamlit_extras==0.4.3

    Alternatively, you can install the dependencies using the provided `requirements.txt` file:


```
pip install -r requirements.txt
```

- **Clone the main repo**

```
cd <FILE LOCATION>

git clone https://github.com/FengboMa/SpectraGuru_beta.git
```

- **Run "Spectra Application Welcome.py"**
- **Run the following command**

```
streamlit run SpectraGuru_beta/Spectra Application Welcome.py
```
- **Your local version should be up in port 8501 by default in your favorite browser!**

---

## About This Project

This project was initiated in June 2024 by Dr. Yiping Zhao and Dr. Xianyan Chen from the University of Georgia as part of a USDA-funded initiative. Learn more [about us](https://www.zhao-nano-lab.com/)!

---

## Help and Support

If you have any questions, comments, or feedback, please reach out to us! Email: zhao-nano-lab@uga.edu.