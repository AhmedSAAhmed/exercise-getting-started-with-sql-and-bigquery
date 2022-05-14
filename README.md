# exercise-getting-started-with-sql-and-bigquery
Training for Kaggle SQL course 
getting-started-bigquery
The repository contains examples of using BigQuery with genomics data. The code within each language-specific folder demonstrates the same set of queries upon the Platinum Genomes dataset. For more detail about this data see Google Genomics Public Data.

Using the BigQuery browser tool
Go to the BigQuery Browser Tool.
Click on "Compose Query".
Copy and paste the following query into the dialog box and click on "Run Query":
#standardSQL
-- Count the number of records (variant and reference segments) we have in
-- the dataset and the total number of calls nested within those records.
--
-- The source data for table genomics-public-data:platinum_genomes.variants
-- was gVCF so a record can be a particular variant or a non-variant segment.
-- https://sites.google.com/site/gvcftools/home/about-gvcf
--
SELECT
  reference_name,
  COUNT(reference_name) AS num_records,
  SUM(ARRAY_LENGTH(call)) AS num_calls
FROM
  `genomics-public-data.platinum_genomes.variants` v
GROUP BY
  reference_name
ORDER BY
  reference_name
View the results!

Query Results

What next?
Work through the Analyze variants using Google BigQuery codelab. The purpose of this codelab is to help you:
learn how to use the Google BigQuery query tool
learn valuable BigQuery SQL syntax
become familiar with the variants table created by a Google Genomics variant export
Try a few more queries in the sql subdirectory.
variant-level-data-for-brca1.sql
sample-level-data-for-brca1.sql
sample-variant-counts-for-brca1.sql
Replace _THE_TABLE_ with genomics-public-data:platinum_genomes.variants or your own table if you have exported variants from Google Genomics to BigQuery.
New to BigQuery?
See the query reference.
See the BigQuery book Google BigQuery Analytics
New to working with variants?
See an overview of the VCF data format.
Looking for more advanced sample queries?
See BigQuery Examples.
Alternate ways to work with BigQuery
Instead of using the browser tool to send queries to BigQuery, you can use code in many languages to call the BigQuery API.

Try the "getting started" samples in one or more languages by navigating to the subdirectory in this repository for the desired language:

RMarkdown
R
All languages will require a Project ID from a project that has the BigQuery API enabled.

Follow the BigQuery sign up instructions if you do not yet have a valid project. (Note: you do not need to enable billing for the small examples in this repository)
You can find the Project ID for your new project in the Google Cloud Console.
For more information on accessing BigQuery from other languages, see: Create A Simple Application With the API
