---
layout: post
title: "Snowflake dbt Weather Pipeline (ELT)"
description: >-
  An ELT pipeline that loads daily weather data for 10 Indian cities into Snowflake and models it with dbt.
skills:
  - Python
  - REST API
  - Snowflake
  - dbt Cloud
  - SQL
  - JSON/VARIANT
  - Git/GitHub
main-image: /cover.png
---

## How it works

1. A Python script calls the Open-Meteo API for each city, covering the past 7 days plus today.
2. The raw JSON is loaded unchanged into a Snowflake `VARIANT` column.
3. A dbt staging model parses it with `LATERAL FLATTEN` and removes duplicates using `ROW_NUMBER` with `QUALIFY`.
4. dbt builds the analytics tables.

## Output tables

| Table | Contents |
|----------|----------|
| dim_city | One row per city with coordinates |
| fct_daily_weather | Daily temperature, rainfall and wind speed |
| fct_monthly_summary | Monthly average high, hottest day and total rainfall |

One run produced 80 daily rows (10 cities x 8 days).

## Data quality

dbt `not_null` tests cover city and date in staging, and `not_null` and `unique` tests cover the city dimension.

## Code

[View on GitHub](https://github.com/Newlin-Anto/Snowflake-DBT-Weather-Pipeline)
