---
layout: default
title: Data Upload
nav_order: 2
---

# Data Upload

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Supported formats

SpectraGuru currently supports the following data formats. 

- Multi files: .txt files (two-column single spectrum files. common x)
- Multi files: .csv files (two-column single spectrum files. common x)
- Single file: .csv file (A tab-separated csv (tsv)file)
- Single file: .csv file (A comma-separated csv (csv)file)

*More formats will be supported in the future*

**A successful upload should trigger Preview after the data upload container.**

### Multi files: .txt files (two-column single spectrum files. common x)

Each file should contain only two columns. The first column should not be the index. It should follow [x y] format. Both columns should be all numerical numbers with the same length. In each batch, all the txt files should have the same number of rows and the same length (x must be the same in each txt file). The second column usually indicates intensity. You could include headers, but it works best with no headers.

NaN and other abnormal values may raise errors and prevent you from moving forward.

**Example**

![image1](../assets/images/data-upload-example1.png)

### Multi files: .csv files (two-column single spectrum files. common x)

Similar to the format above, but everything is in CSV format. You could include headers, but work the best with no headers.

NaN and other abnormal values may raise errors and prevent you from moving forward.
