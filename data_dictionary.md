# Data Dictionary and Dataset Limitations

## 1. Dataset Source

This project uses **Student Performance Factors**, published
on Kaggle by `lainguyn123`.

Source: https://www.kaggle.com/datasets/lainguyn123/student-performance-factors

The project dataset contains 6,607 records and 20 original
columns describing study habits, attendance, educational
support, student characteristics and exam performance.

- Raw file: `data/raw/StudentPerformanceFactors.csv`
- Cleaned file: `data/processed/StudentPerformanceFactors_cleaned.csv`
- Outcome variable: `Exam_Score`

The column definitions below follow the publisher's
**About Dataset** description.

### How the Dataset Was Produced

The supplied publisher description does not explain the
collection or generation method, sampling process, location,
collection dates or participating institutions.

It also does not establish whether the records were collected
from real students or generated synthetically. These details
are therefore treated as unknown.

Project cleaning and transformation steps are documented in
the notebooks. The cleaned CSV is a project output, separate
from the original downloaded file.

## 2. Column Definitions

| Column | Type | Description and units or categories |
| --- | --- | --- |
| Hours_Studied | Numerical | Hours spent studying per week. |
| Attendance | Numerical | Percentage of classes attended. |
| Parental_Involvement | Categorical, ordinal | Parental involvement in education: Low, Medium, High. |
| Access_to_Resources | Categorical, ordinal | Availability of educational resources: Low, Medium, High. |
| Extracurricular_Activities | Categorical, binary | Participation in extracurricular activities: Yes, No. |
| Sleep_Hours | Numerical | Average hours of sleep per night. |
| Previous_Scores | Numerical | Scores from previous exams; the grading scale is not specified. |
| Motivation_Level | Categorical, ordinal | Student motivation: Low, Medium, High. |
| Internet_Access | Categorical, binary | Availability of internet access: Yes, No. |
| Tutoring_Sessions | Numerical, count | Number of tutoring sessions attended per month. |
| Family_Income | Categorical, ordinal | Family income level: Low, Medium, High. |
| Teacher_Quality | Categorical, ordinal | Teacher quality: Low, Medium, High. |
| School_Type | Categorical, nominal | School type: Public, Private. |
| Peer_Influence | Categorical | Peer influence on academic performance: Positive, Neutral, Negative. |
| Physical_Activity | Numerical | Average hours of physical activity per week. |
| Learning_Disabilities | Categorical, binary | Recorded presence of learning disabilities: Yes, No. |
| Parental_Education_Level | Categorical, ordinal | Highest parental education level: High School, College, Postgraduate. |
| Distance_from_Home | Categorical, ordinal | Distance from home to school: Near, Moderate, Far. |
| Gender | Categorical, nominal | Recorded gender: Male, Female. |
| Exam_Score | Numerical | Final exam score, used as the prediction target; the grading scale is not specified. |

The original dataset contains seven numerical variables and
13 categorical variables.

The publisher does not specify monetary thresholds for income,
distance thresholds, or how categories such as teacher quality
and motivation were assessed.

Any grouped variables, encoded features or Power BI measures
created during the project are derived fields rather than
original dataset columns.

## 3. Dataset and Analytical Limitations

### Unknown Representativeness

Without a documented sampling or generation process, it is
not possible to establish which student population the data
represents. Findings should not automatically be generalised
to particular schools, countries or education systems.

### Broad Categories and Missing Context

Categories such as Low, Medium and High simplify complex
characteristics and hide differences within each group.

The original columns do not include age, school year, exam
subject, institution or collection date. These omissions
limit contextual interpretation.

### Data Quality and Cleaning

Missing-value treatment and other cleaning decisions can
affect distributions, associations and model results.
The notebooks document the project's treatment of these issues.

The analysis identified an Exam_Score value of 101. Because
the publisher does not specify the grading scale, this value
cannot be assumed invalid solely because it exceeds 100.
Its treatment should follow the documented cleaning decision.

### Aggregation and Model Interpretation

Averages can conceal variation between students. Deep
decomposition-tree branches may describe small subgroups
whose averages are less stable.

Pearson correlation measures linear relationships. Values
near zero do not rule out non-linear relationships.

Regression results depend on the model specification.
Permutation importance measures a fitted model's dependence
on predictors for its evaluation performance; it is not a
percentage contribution to exam scores.

### Association Does Not Prove Causation

Relationships in this dataset do not establish cause and effect.

For example, higher attendance is associated with higher exam
scores, but this does not prove that increasing attendance
alone will produce the predicted score difference.

Other factors may influence both variables. Adjusting for
selected variables does not eliminate all possible confounding.
The same caution applies to group comparisons, correlations
and feature importance.

## 4. Ethical Considerations

### Sensitive Information and Fairness

Gender, family income and learning disabilities are potentially
sensitive characteristics. Findings should not be used to
stereotype students or justify discriminatory treatment.

The available categories are simplified. Binary gender and
disability fields do not capture the full diversity of students
or their support needs.

Overall model performance does not establish equal accuracy
across different student groups.

### Privacy

The original columns contain no names or direct student
identifiers. This alone does not guarantee that records could
never be re-identified.

The project does not attempt to identify individuals or link
records to external personal information.

### Responsible Use and Transparency

This project is intended for educational analysis. Its findings
should not be used alone to make admissions, grading,
disciplinary or support-allocation decisions.

Any real-world application would require verified provenance,
appropriate permissions, external validation and fairness checks.

The project credits the dataset publisher and documents its
methods and limitations. Observed data, cleaned values and
model predictions should be clearly distinguished.