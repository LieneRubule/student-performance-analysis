# Data Dictionary, Provenance and Limitations

## Dataset Overview

This project uses the Student Performance Factors dataset,
published on Kaggle by `lainguyn123`.

- Source: https://www.kaggle.com/datasets/lainguyn123/student-performance-factors
- Project dataset: 6,607 records and 20 original columns.
- Unit of analysis: one student record.
- Outcome variable: `Exam_Score`.
- Raw file: `data/raw/StudentPerformanceFactors.csv`.
- Cleaned file: `data/processed/StudentPerformanceFactors_cleaned.csv`.

The original columns comprise seven numerical variables and
13 categorical variables.

## Dataset Provenance

The dataset was obtained from Kaggle rather than collected
directly for this project.

The original collection or generation process has not been
independently verified. The project does not establish the
sampling method, collection dates, location, participating
institutions or whether the records represent real students
or were synthetically generated.

These uncertainties limit claims about representativeness.
The dataset is used for educational analysis and modelling,
not as verified evidence about a particular school population.

The project's cleaning and preparation steps are documented
in the notebooks. The processed CSV is a project output and
should be distinguished from the original downloaded data.

## Column Definitions

Units that have not been verified against the publisher's
description are identified explicitly.

| Column | Type | Description | Units or categories |
| --- | --- | --- | --- |
| Hours_Studied | Numerical | Time spent studying. | Hours; reporting period requires source verification. |
| Attendance | Numerical | Proportion of classes attended. | Percentage (%). |
| Parental_Involvement | Categorical, ordinal | Recorded level of parental involvement in education. | Low, Medium, High. |
| Access_to_Resources | Categorical, ordinal | Recorded availability of educational resources. | Low, Medium, High. |
| Extracurricular_Activities | Categorical, binary | Whether the student participates in extracurricular activities. | No, Yes. |
| Sleep_Hours | Numerical | Recorded duration of sleep. | Hours; reporting period requires source verification. |
| Previous_Scores | Numerical | Recorded previous academic assessment score. | Score points; assessment and grading scale require verification. |
| Motivation_Level | Categorical, ordinal | Recorded level of motivation. | Low, Medium, High. |
| Internet_Access | Categorical, binary | Whether internet access is recorded as available. | No, Yes. |
| Tutoring_Sessions | Numerical, count | Number of tutoring sessions attended. | Sessions; reporting period requires source verification. |
| Family_Income | Categorical, ordinal | Recorded household income category. | Low, Medium, High; monetary thresholds are unverified. |
| Teacher_Quality | Categorical, ordinal | Recorded teaching-quality category. | Low, Medium, High; rating method is unverified. |
| School_Type | Categorical, nominal | Type of school attended. | Public, Private. |
| Peer_Influence | Categorical | Recorded direction of peer influence. | Negative, Neutral, Positive. |
| Physical_Activity | Numerical | Recorded amount of physical activity. | Measurement unit and reporting period require source verification. |
| Learning_Disabilities | Categorical, binary | Whether a learning disability is recorded. | No, Yes; diagnostic criteria are unverified. |
| Parental_Education_Level | Categorical, ordinal | Recorded parental education category. | High School, College, Postgraduate. |
| Distance_from_Home | Categorical, ordinal | Recorded home-to-school distance category. | Near, Moderate, Far; distance thresholds are unverified. |
| Gender | Categorical, nominal | Gender category recorded in the dataset. | Female, Male. |
| Exam_Score | Numerical | Final exam score used as the outcome in this project. | Score points; the exact grading scheme requires verification. |

Category labels describe how the dataset is encoded. They do
not establish objective definitions of concepts such as
motivation, teacher quality or parental involvement.

## Original and Derived Variables

The table above describes the 20 original dataset columns.

Any grouped variables created during analysis, model-encoded
features or Power BI measures are derived variables. Their
definitions belong alongside the relevant transformation code.

Display labels such as "Hours Studied" replace underscores for
readability without changing the meaning of the original field.

## Data Quality and Limitations

### Missing Data and Cleaning

Missing-value handling can change distributions, relationships
and uncertainty estimates.

Imputed values are estimates rather than observed measurements.
The cleaning notebook should be consulted for the exact columns,
methods and number of affected records.

If missing outcome values are imputed, those outcomes should not
be treated as equivalent to independently observed exam scores
when assessing predictive performance.

### Uncertain Provenance

The collection or generation process is not independently
verified. Results cannot automatically be generalised to real
students, specific countries or particular education systems.

### Measurement and Category Definitions

Several variables use broad categories. These simplify complex
characteristics and may conceal substantial differences within
each group.

Unverified reporting periods and category thresholds restrict
precise interpretation. For example, a tutoring-session count
cannot be described as weekly or monthly without confirmation.

### Score Validity

The analysis has reported an Exam_Score value of 101.
The grading scheme must be checked before assuming that scores
are strictly bounded between 0 and 100.

Unusual values should be documented and investigated rather
than automatically removed or capped.

### Missing Context

The original columns do not identify student age, school year,
exam subject, institution or collection date.

These omissions limit comparisons and prevent assessment of
some potentially important contextual differences.

### Group Size and Aggregation

Overall averages can conceal variation between students.
Filters and deeper decomposition-tree branches may produce
small subgroups whose averages are less stable.

### Statistical and Model Limitations

Pearson correlation describes pairwise linear relationships.
A correlation close to zero does not rule out a non-linear
relationship.

Regression estimates depend on model assumptions and the
variables included. Adjustment does not eliminate all possible
confounding.

Permutation importance measures the fitted model's dependence
on a predictor for the selected evaluation metric. It is not
a causal effect or a percentage contribution to exam scores.

## Ethical Considerations

### Sensitive Characteristics

The dataset contains potentially sensitive information,
including learning disabilities, gender and family income.

These variables must not be used to label students as less
capable or to justify discriminatory treatment.

### Fairness and Representation

The available categories may not represent the full diversity
of students. For example, Gender contains only Female and Male,
while Learning_Disabilities uses a simple Yes/No classification.

A model's overall accuracy does not demonstrate equal performance
across different student groups.

### Privacy

The original columns contain no names or direct student
identifiers. However, absence of direct identifiers does not
prove that re-identification is impossible.

The project does not attempt to identify individuals or link
records to external personal information.

### Appropriate Use

This is an educational analysis project. Its results should not
be used alone to determine admissions, grades, disciplinary
actions or access to support.

Any real-world use would require verified provenance,
appropriate permissions, external validation and fairness
assessment.

### Transparency

The project should acknowledge the dataset publisher, document
cleaning decisions and distinguish observed values from
estimated or model-predicted values.

Results should be communicated with their limitations rather
than presented as universal facts about students.

## Associations Do Not Prove Cause and Effect

An association means that variables vary together in this
dataset. It does not establish that changing one variable
will cause another to change.

For example, higher attendance may be associated with higher
exam scores. This does not prove that increasing attendance
alone will produce the model's predicted score difference.

Other factors may influence both attendance and exam performance.
Statistical adjustment only accounts for the variables included
in the model and does not establish causation.

The same caution applies to correlations, differences between
student groups and model feature importance.

## Documentation Checks Still Required

- Verify numerical units and reporting periods against the
  publisher's data description.
- Confirm any available information about data collection
  or synthetic generation.
- Check the grading scale and treatment of Exam_Score = 101.
- Confirm that the cleaning description matches the notebook.
