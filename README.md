# ELITE Data Analyst Assignment

## Task 1
Given the `events` CTE with columns `id`, `occur_time`, and `close_time`, 
write a SQL query to generate `task_id` for events occurring before their corresponding close times.
The `task_id` should be assigned based on the chronological order of the events. 
If there are multiple events with the same `id` and overlapping time intervals, they should be considered as a single task. 
The result should display the `id`, `task_id` **earliest** `occur_time` and **latest** `close_time` for each task.

### Output
```sql
┌────┬─────────┬────────────┬────────────┐
│ id ┆ task_id ┆ occur_time ┆ close_time │
╞════╪═════════╪════════════╪════════════╡
│  1 ┆       1 ┆ 08:00:00   ┆ 08:51:00   │
│  1 ┆       2 ┆ 08:55:00   ┆ 10:50:00   │
│  2 ┆       1 ┆ 08:00:00   ┆ 08:55:00   │
└────┴─────────┴────────────┴────────────┘
```

### Query
Please use [DuckDB Wasm](https://shell.duckdb.org/) to run the query.
```sql
WITH events(id, occur_time, close_time) AS (
    VALUES
    (1, '09:00:00', '10:00:00'),
    (1, '09:00:00', '09:20:00'),
    (1, '09:10:00', '09:50:00'),
    (1, '08:55:00', '09:50:00'),
    (1, '08:00:00', '08:51:00'),
    (1, '08:10:00', '08:50:00'),
    (1, '09:10:00', '10:50:00'),
    (2, '08:00:00', '08:55:00'),
    (2, '08:10:00', '08:50:00')
)
-- Your query here...
```


## Task 2
Using data from [BigQuery sample dataset for GA4](https://console.cloud.google.com/bigquery?project=bigquery-public-data&p=bigquery-public-data&d=ga4_obfuscated_sample_ecommerce&page=dataset) (You can access the data freely via [BigQuery Sandbox](https://cloud.google.com/bigquery/docs/quickstarts/query-public-dataset-console)),
create the following queries:

### I. Daily (N-Day) Retention Query

   Write a SQL query to calculate the daily retention of users.
   The query should consider user retention on a daily basis,
   it should show the percentage of users who returned on each subsequent day
   after their initial visit.

### II. Daily Unbounded Retention Query

   Write a SQL query to calculate the daily unbounded retention of users.
   The query should consider user unbounded retention on a daily basis,
   it should show the percentage of users who came back on a specific day
   or _anytime after that day_ following their initial visit. 
   For example, for all new users who visited on a specific day,
   what percentage of users came back after 28 days (and not necessarily on day 28).

Please note that you should utilize the `ga4_obfuscated_sample_ecommerce` dataset provided in BigQuery for both queries. 
Feel free to use any relevant tables and columns available in the dataset to accomplish the task. 
Provide clear aliases for the output columns, and ensure to provide explanations for any significant steps 
or calculations in your queries to demonstrate your understanding of the process.

### Output Columns
```sql
┌────────────────────┬───────┬──────┬──────────┬────────────────┐
│ initial_visit_date ┆ users ┆ days ┆ retained ┆ retention_rate │
╞════════════════════╪═══════╪══════╪══════════╪════════════════╡

```

## Task 3
Using data from [BigQuery sample dataset for GA4](https://console.cloud.google.com/bigquery?project=bigquery-public-data&p=bigquery-public-data&d=ga4_obfuscated_sample_ecommerce&page=dataset),
build a dashboard using Looker Studio.

Ensure that the dashboard is visually appealing, easy to understand, and allows users to interact with the data. 
Use appropriate data visualization techniques. Feel free to be creative and add additional visualizations or features that you believe will provide valuable insights.


## Evaluation Criteria

The evaluation will take into account the completeness and correctness of the solutions, 
as well as the quality of the dashboard and accompanying documentation. 
The candidate will be assessed based on their SQL skills, data visualization and/or dashboarding techniques.


