---
layout: post
title: "End-to-End Data Engineering Pipeline on AWS"
description: >-
  PySpark pipelines on AWS EC2 that move employee data from an S3 Bronze layer to Silver and Gold layers in Parquet.
skills:
  - AWS EC2
  - Amazon S3
  - PySpark
  - Python
  - Ubuntu Linux
  - Parquet
  - Git/GitHub
main-image: /cover.png
---

## How it works

1. Raw employee and performance CSV files sit in the S3 Bronze layer.
2. PySpark on an Ubuntu EC2 instance reads them through the `s3a` connector.
3. Duplicates and rows with missing values are removed. Salaries must be above 0 and ratings between 0 and 5.
4. Bonus and salary-level columns are added.
5. Results are written to the Silver and Gold layers in Parquet.

## Joins and analysis

I practised inner, left, right, full outer and left anti joins on the employee and performance data.

## Gold datasets

| Dataset | Contents |
|----------|----------|
| DepartmentSummary | Headcount and salary figures by department |
| EmployeePerformance | Employees matched with performance records |
| DepartmentReport | Average rating, salary and experience by department |
| EmployeeWithoutPerformance | Employees with no performance record |

## Code

[View on GitHub](https://github.com/Newlin-Anto/End-to-End-Data-Engineering-Pipeline-on-AWS)
