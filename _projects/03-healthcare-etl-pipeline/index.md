---
layout: post
title: "Healthcare ETL Pipeline using PySpark and Hadoop"
description: >-
  A modular ETL pipeline on Hadoop HDFS that cleans healthcare data and produces analytical datasets in Parquet.
skills:
  - Python
  - PySpark
  - Apache Spark
  - Hadoop HDFS
  - Linux
  - Parquet
  - Git/GitHub
main-image: /cover.png
---

## How it works

Separate extract, transform, process and load modules run from one driver script.

1. **Extract:** read the raw healthcare CSV from HDFS.
2. **Transform:** profile duplicates, age range, billing and dates, then remove duplicates and non-positive billing records and standardise patient names.
3. **Process:** calculate stay duration and age groups, and build summaries.
4. **Load:** write the results to HDFS as Parquet.

## Output datasets

| Dataset | Contents |
|----------|----------|
| patient_data | Cleaned records with stay duration and age group |
| hospital_summary | Patient count, billing and average stay by hospital |
| insurance_summary | Patient count and billing by insurance provider |

## Code

[View on GitHub](https://github.com/Newlin-Anto/Healthcare-ETL-Pipeline)
