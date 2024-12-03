# Preparing Data for Modeling - Customer Analytics 

A common challenge in developing models to extract business value from data is the large size of the datasets, which can lead to prediction times spanning several days. Optimizing the storage of these datasets is essential to enable faster model execution without sacrificing data volume.

This project aims to clean up one of their largest customer datasets, which will ultimately support predictions about whether students are seeking new job opportunities. This information will help guide students toward potential recruiters.

The access to `customer_train.csv`- a sample from the full customer dataset is provided. The objective is to create a proof-of-concept for a more efficient storage solution. The dataset includes anonymized student information and labels indicating whether they were job-seeking during the training period:

| Column                   | Description                                                                      |
|------------------------- |--------------------------------------------------------------------------------- |
| `student_id`             | A unique ID for each student.                                                    |
| `city`                   | A code for the city the student lives in.                                        |
| `city_development_index` | A scaled development index for the city.                                         |
| `gender`                 | The student's gender.                                                            |
| `relevant_experience`    | An indicator of the student's work relevant experience.                          |
| `enrolled_university`    | The type of university course enrolled in (if any).                              |
| `education_level`        | The student's education level.                                                   |
| `major_discipline`       | The educational discipline of the student.                                       |
| `experience`             | The student's total work experience (in years).                                  |
| `company_size`           | The number of employees at the student's current employer.                       |
| `company_type`           | The type of company employing the student.                                       |
| `last_new_job`           | The number of years between the student's current and previous jobs.             |
| `training_hours`         | The number of hours of training completed.                                       |
| `job_change`             | An indicator of whether the student is looking for a new job (`1`) or not (`0`). |

The task is to create a DataFrame, named `ds_jobs_transformed`, that efficiently stores the data from `customer_train.csv`. The following requirements have been specified:

- Columns with only two categorical factors must be stored as Booleans (bool).
- Columns containing only integers must be stored as 32-bit integers (int32).
- Columns containing floating-point values must be stored as 16-bit floats (float16).
- Nominal categorical data must be stored using the category data type.
- Ordinal categorical data must be stored as ordered categories, maintaining their natural order, without mapping to numerical values.
- The DataFrame must be filtered to include only students with at least 10 years of experience at companies employing 1,000 or more people, as the recruiter base targets experienced professionals at enterprise-level organizations.

When .info() or .memory_usage() methods are called on ds_jobs and ds_jobs_transformed, a significant reduction in memory usage should be observed after preprocessing.