# Dashboard Planning and Design

**Project:** Student Performance Analysis  
**Dashboard file:** `powerbi/Student_Performance_Dashboard.pbix`  
**Updated:** 12 October 2026

## Purpose

The Power BI dashboard presents the student performance analysis
across four pages. It combines summary measures, model feature
importance, hypothesis findings, interactive group exploration
and numerical correlations.

The report is designed to make the analysis understandable to
users without requiring them to read the Python notebooks.

## Report Structure

| Page | Main content |
| --- | --- |
| Overview | Summary cards, attendance chart, feature importance and slicers |
| Hypothesis Findings | Three bookmark-controlled hypothesis views |
| Explore Performance | Interactive decomposition tree |
| Correlations | Numerical correlation matrix with heatmap formatting |

## Page 1 — Overview

**Page heading:** Student Performance Overview

### Layout

Four summary cards run across the top of the page.

The attendance chart is positioned on the left, with six student
slicers arranged beneath it in two rows.

The feature importance chart occupies the centre-right area.
A tall factor-selection slicer sits beside it on the far right.

### Summary Cards

| Measure | Unfiltered value |
| --- | --- |
| Student Count | 6,607 |
| Average Exam Score | 67.24 |
| Average Attendance | 80.0% |
| Average Study Hours | 20.0 |

### Attendance Chart

**Title:** Average Exam Score and Student Count  
**Subtitle:** by Attendance

This combination chart displays:

- Light purple columns for average exam score.
- A dark purple line for student count.
- Attendance on the horizontal axis.
- Separate vertical scales for exam score and student count.

Showing both measures provides context for the average exam
scores at different attendance levels.

### Student Slicers

The six slicers beneath the attendance chart are:

| Slicer | Options |
| --- | --- |
| Gender | Female, Male |
| School Type | Private, Public |
| Internet Access | No, Yes |
| Learning Disabilities | No, Yes |
| Peer Influence | Negative, Neutral, Positive |
| Extracurricular Activities | No, Yes |

These controls support exploration of student-level measures.
Their configured interactions should be checked during final testing.

### Feature Importance Chart

**Title:** What Predicts Exam Performance?

**Subtitle:** Model feature importance — use the factor selector
to compare predictors.

The horizontal bar chart displays model permutation importance,
ordered from highest to lowest. Attendance and Hours Studied
have the largest displayed importance values.

**Horizontal axis:** Decrease in test R² (percentage points)

The values represent the average decrease in test R² when a
predictor is shuffled, multiplied by 100 for readability.
Permutation importance is calculated over 30 repeats.

A displayed value of 20 means a decrease of 0.20 in test R².
It does not represent a 20-mark increase in exam score or a
20% share of total importance.

### Factor Selection

The **Choose factors** slicer contains checkboxes for individual
predictors and a **Select all** option.

It allows users to display selected factors together for comparison.

The importance values are imported model results. Student
slicer selections do not retrain the model or recalculate these
Python-generated values.

## Page 2 — Hypothesis Findings

**Page heading:** What shapes exam performance?

### Layout and Navigation

Three buttons appear below the heading:

- H1 · Attendance.
- H2 · Tutoring.
- H3 · Resources.

Bookmarks switch between the three hypothesis views on the
same report page.

The selected button is highlighted in purple. Each view places
a chart on the left and a **MAIN FINDING** panel on the right.

### H1 — Attendance

**Chart title:** Attendance and predicted exam score

A purple column chart shows predicted exam scores at attendance
levels of 60, 70, 80, 90 and 100.

The displayed score labels are approximately 63, 65, 67, 69 and 71.

**Main finding:** +1.99 exam-score points

The explanation states that this difference is associated with
10 percentage points higher attendance, accounting for study
hours and previous scores.

### H2 — Tutoring

**Chart title:** Tutoring and predicted exam scores

**Subtitle:** Comparison at previous scores of 63, 75 and 88.

A line chart compares predicted exam scores across zero to five
tutoring sessions for three previous-score levels:

- Previous score: 63
- Previous score: 75
- Previous score: 88

The three coloured lines show similar upward patterns.

**Main finding:** Similar tutoring patterns

The accompanying explanation states that there is no clear
evidence that the relationship between tutoring and exam scores
varies with previous scores.

**Displayed interaction p-value:** 0.805

### H3 — Resources

**Chart title:** Resource access and exam scores.

**Subtitle:** Adjusted score difference vs low access.

A purple column chart compares High and Medium resource access
with the Low access reference group.

| Resource access | Adjusted score difference versus Low |
| --- | --- |
| High | +1.84 points |
| Medium | +0.88 points |

**Main finding:** +1.84 exam-score points

The explanation identifies this as the difference between High
and Low resource access, accounting for family income and
previous scores. A second statement reports the Medium versus
Low difference of +0.88 points.

### Interpretation

This page presents the exported statistical findings.
The bookmark buttons change the displayed hypothesis rather
than rerunning the statistical models.

Adjusted predictions and group differences are distinct from
the descriptive averages used elsewhere in the dashboard.

## Page 3 — Explore Performance

**Page heading:** Explore Student Performance

**Visual title:** Explore Exam Scores by Student Factors

### Layout

A single wide decomposition tree occupies the main area beneath
the page heading.

The small study-hours line chart has been removed, leaving the
page focused on interactive exploration.

### Analysed Measure

The tree starts with the overall average exam score of **67.24**.

Users can explore how this average differs across student groups
by selecting branches and expanding additional factors.

### Factors Shown in the Expanded View

The supplied dashboard view contains these eight factors:

1. Access to Resources
2. Parental Involvement
3. Motivation Level
4. School Type
5. Family Income
6. Parental Education Level
7. Teacher Quality
8. Distance from Home

Purple bars, connecting lines and bold selected labels show the
current exploration path.

### Interpretation

Each additional split applies within the previously selected
groups. Values further along the tree therefore describe a
specific combination of student characteristics.

The tree displays descriptive averages. It is not a visualisation
of the trained prediction model and does not establish causation.

## Page 4 — Correlations

**Page heading:** Correlations Between Numerical Variables

**Matrix title:** How Student Factors Correlate?

**Subtitle:** Pearson correlation (r): −1 = negative,
0 = no linear relationship, +1 = positive.

### Layout

A large matrix sits beneath the heading, with its title and
explanatory subtitle directly above it.

The matrix displays correlation coefficients to two decimal
places and uses coloured cell backgrounds to show their strength
and direction.

### Variables and Order

The same seven variables appear across the columns and down
the rows in this order:

1. Attendance
2. Exam Score
3. Hours Studied
4. Physical Activity
5. Previous Scores
6. Sleep Hours
7. Tutoring Sessions

### Data Source

The correlations are calculated in:

`jupyter_notebooks/Student_Performance_EDA.ipynb`

They are exported to:

`data/processed/numerical_correlations.csv`

The Power BI matrix uses:

| Matrix area | Field |
| --- | --- |
| Rows | Row_Factor |
| Columns | Column_Factor |
| Values | Correlation |

The exported table contains 49 variable pairs.

### Formatting

- Positive correlations use purple shading.
- Values close to zero have pale, near-white backgrounds.
- The diagonal displays 1.00 for each variable's correlation with itself.
- Numerical labels remain visible inside the cells.
- Row and column totals are removed.
- Purple borders separate the matrix headers and cells.

The colour scale is configured around −1, 0 and +1.

### Displayed Relationships with Exam Score

| Variable | Pearson correlation with Exam Score |
| --- | --- |
| Attendance | 0.58 |
| Hours Studied | 0.45 |
| Previous Scores | 0.18 |
| Tutoring Sessions | 0.16 |
| Physical Activity | 0.03 |
| Sleep Hours | −0.02 |

Attendance and Hours Studied show the strongest positive
pairwise correlations with Exam Score among these variables.

The matrix contains precomputed correlations. It does not
recalculate subgroup correlations when student filters change.

## Shared Visual Design

The dashboard uses a consistent purple theme:

- Dark purple banners with bold white page headings.
- Pale backgrounds with soft purple and blue tones.
- White chart and content areas.
- Purple chart elements, borders and selected controls.
- Rounded cards, slicer containers and navigation buttons.

The four report tabs provide navigation between the pages.
Within Hypothesis Findings, bookmark buttons provide navigation
between the three statistical results.

## Design Rationale

The Overview provides a quick summary and predictor comparison.

Hypothesis Findings keeps the statistical explanations together,
using one chart and one main finding at a time to avoid crowding.

Explore Performance gives the decomposition tree enough width
for users to follow combinations of student characteristics.

Correlations gives the numerical relationships a dedicated page
with both values and colour shading.

## Interpretation Boundaries

The dashboard presents three different types of analytical output:

- Descriptive averages summarise student groups.
- Adjusted statistical results account for specified variables.
- Permutation importance measures the fitted model's dependence
  on predictors for test performance.

Pearson correlations describe pairwise linear relationships.
These measures answer different questions and should not be
interpreted as interchangeable or causal.

## Final Checks

- Check that all three hypothesis buttons display the correct
  chart, finding panel and selected-button colour.
- Verify the student slicer interactions.
- Test selecting and clearing factors in the importance chart.
- Test expanding and changing decomposition tree branches.
- Check displayed values against the notebook exports.
- Check text readability and tooltips at normal viewing size.
- Save the intended opening view for each page.
- Save the PBIX file and commit the dashboard documentation.