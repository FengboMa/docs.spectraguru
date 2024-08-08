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

## Support format

SpectraGuru currently support following data formate. 

- Multi files: .txt files (two-column single spectrum files. common x)
- Multi files: .csv files (two-column single spectrum files. common x)
- Single file: .csv file (A tab-separated csv (tsv)file)
- Single file: .csv file (A comma-separated csv (csv)file)

*More formats will be support in future*

A successful upload should trigger Preview after the data upload container.

### Multi files: .txt files (two-column single spectrum files. common x)

Each file should contain only two columns. No index on the first column. It should follow [x y] formate. Both column should be all numerical numbers with same length. In each batch, all the txt files should have same number of rows and same length (x must be the same in each txt files). The second column usually indicates intensity. You could include headers, but work the best with no headers.

NaN and other abnormal values may raise error and prevent you from moving forward.

**Example**
![]("../../assets/images/data-upload-example1.png")

### Multi files: .csv files (two-column single spectrum files. common x)

Similar to the formate above but everything in csv formate. You could include headers, but work the best with no headers.

NaN and other abnormal values may raise error and prevent you from moving forward.
