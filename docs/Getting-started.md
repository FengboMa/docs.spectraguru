---
layout: default
title: Getting started
nav_order: 3
---

# Getting started

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Quick start

### Visit our site

{: .note }
Aug 16, 2024. For UGA internal usage. Connect to school local area network (LAN), i.e. school Wi-Fi PAWS-Secure. And visit [here](http://172.19.194.69:8501)!

Our application is hosted [space holder](https://www.youtube.com/watch?v=dQw4w9WgXcQ)! Please use it directly, as easy as it can go.

### Deploy locally

You do not have to host it locally to use the application. But if you wish to deploy it locally, please follow these steps:

- **Install Python and dependencies**
   
   SpectraGuru runs on:

       altair==5.3.0

       deprecation==2.1.0

       matplotlib==3.8.4

       numpy==1.23.5

       pandas==2.2.2

       scikit_learn==1.5.1

       scipy==1.14.0

       streamlit==1.35.0

       streamlit_extras==0.4.3

    Or use requirements.txt to install the dependencies: 

```
pip install -r requirements.txt
```

- **Clone the main repo**

```
cd <FILE LOCATION>

git clone https://github.com/FengboMa/SpectraGuru_beta.git
```

- **Run Spectra Application Welcome.py**
- **Run the following command**

```
streamlit run SpectraGuru_beta/Spectra Application Welcome.py
```
- **Your local version should be up in port 8501 by default in your favorite browser!**

---

## About this Project
The project was started in Jun 2024 by Dr. Yiping Zhao and Dr. Xianyan Chen from the University of Georgia as a part of a USDA-funded project. See more [about us](https://www.zhao-nano-lab.com/)!

---

## Help and Support

If you have any questions, comments, and observations, please let us know! Email: zhao-nano-lab@uga.edu.