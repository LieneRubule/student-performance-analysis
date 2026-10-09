# Power BI Dashboard Plan

## Purpose and Audience

The dashboard will help teachers and education support staff explore student performance and factors associated with exam scores.

It will use the cleaned dataset and present descriptive relationships. Associations will not be described as proof of cause and effect.

## Visual Style and Navigation

- Light lavender page backgrounds with white chart panels.
- Purple and teal as the main theme, with additional distinct colours for the six factor lines.
- Rounded summary cards, dark readable text and consistent spacing.
- Clear titles, labelled axes and short explanations.
- Colour supported by labels and markers.
- A navigation strip linking Overview, Attendance & Study, and Resources & Support.
- Clearly visible filters and a Reset filters button on every page.

## Stakeholder Questions and Visuals

| Page | Stakeholder question | Planned visual |
|---|---|---|
| Overview | How many students are represented, and what are the overall averages? | Summary cards |
| Overview | How are exam scores distributed? | Histogram |
| Overview | What proportion of students attends each school type? | Donut chart |
| Attendance & Study | How does attendance relate to exam performance? | Scatter plot |
| Attendance & Study | How do numerical factor profiles differ across exam-score bands? | Multiple-factor line chart |
| Resources & Support | How do average scores vary across combinations of family income and resource access? | Colour-shaded matrix |
| Resources & Support | How do average scores and student counts vary by tutoring sessions? | Combination chart: columns and an overlapping line |

## Page 1 — Overview

### Layout Sketch

| Position | Planned content |
|---|---|
| Top | Title, introduction and navigation |
| Filter row | Gender and School Type slicers; Reset filters |
| Summary row | Student count, average exam score, average attendance and average study hours |
| Main area — left | Exam-score histogram |
| Main area — right | School-type donut chart |
| Bottom | Short findings and data-limitations note |

### Design Decisions

Summary cards will provide a quick introduction to the selected sample.

The histogram will show student counts in ordered exam-score bands, including the retained score of 101.

The donut chart will show school-type proportions with labels and percentages. Its small number of categories makes this format readable.

## Page 2 — Attendance & Study

### Layout Sketch

| Position | Planned content |
|---|---|
| Top | Title and navigation |
| Filter row | Gender, Attendance and Study Hours slicers; Reset filters |
| Upper area — left | Attendance versus exam score scatter plot |
| Upper area — right | Brief chart explanations and factor-selection control |
| Lower area — full width | Multiple-factor line chart |

### Attendance Scatter Plot

- Horizontal axis: attendance (%).
- Vertical axis: exam score in points.
- Show individual observations with small, partly transparent markers.
- Use tooltips to display attendance and exam score.
- Preserve individual records when preparing the visual.

This chart will show the spread of results as well as the overall relationship.

### Multiple-Factor Line Chart

**Title:** Student Factor Profiles by Exam-Score Band

- Horizontal axis: ordered exam-score bands.
- Vertical axis: average normalised factor value (0–100).
- Separate coloured lines for:
  - Attendance
  - Hours Studied
  - Sleep Hours
  - Previous Scores
  - Tutoring Sessions
  - Physical Activity
- Use visible markers and a clearly labelled legend.
- Allow users to select which factors to display.
- Tooltips will include the factor name, original-unit average, normalised average and student count.

Each factor will be scaled using its minimum and maximum in the full cleaned dataset:

Normalised value = 100 × (value − minimum) / (maximum − minimum)

Normalised values will then be averaged within each exam-score band. The scaling reference will remain fixed when filters change.

The scale compares relative factor levels. It does not represent percentage effect, importance or causation. Equal normalised values for different factors do not imply equal educational meaning.

Lines connect ordered score bands, not points in time. Empty bands will not be displayed as zero, and tooltips will identify small groups.

The chart will use the full page width to keep six lines readable.

## Page 3 — Resources & Support

### Layout Sketch

| Position | Planned content |
|---|---|
| Top | Title and navigation |
| Filter row | Family Income and Resource Access slicers; Reset filters |
| Main area — left | Colour-shaded income/resource matrix |
| Main area — right | Tutoring combination chart |
| Bottom | Explanations and small-group warning |

### Colour-Shaded Matrix

- Rows: family income — Low, Medium, High.
- Columns: resource access — Low, Medium, High.
- Cell values: average exam score.
- Cell shading: a consistent light-to-dark scale representing average score.
- Tooltips: average score and student count.
- Empty combinations will remain blank.

The nine combinations will let users compare resource access and family income together. Printed values will support the colour shading.

Use a consistent colour scale under filtering so the same colour retains the same meaning.

### Tutoring Combination Chart

- Horizontal axis: tutoring-session count.
- Purple columns: student count.
- Teal line with markers: average exam score.
- Left vertical axis: student count, starting at zero.
- Right vertical axis: average exam score in points.
- Tooltips: tutoring sessions, student count and average exam score.

The overlaid styles will show both the average result and how many students support it.

Axes will be clearly labelled because counts and scores use different units. The heights of the columns and line are not directly comparable.

A note will explain that averages for small groups, particularly at higher tutoring-session counts, can be unstable.

## Interactivity

- Slicers will update the relevant charts and summary cards.
- Selecting chart elements will filter or highlight related visuals where meaningful.
- Hover tooltips will provide values and group counts.
- A factor selector will control the lines displayed in the factor-profile chart.
- Navigation buttons will connect all three pages.
- Reset buttons will restore each page's default view.
- Each page's filters will apply to that page unless explicitly configured otherwise.
- Filter controls and selection states will remain visible.

If reshaping data is needed for the factor-profile chart, student counts and other summaries must remain accurate and must not count repeated factor rows as additional students.

## Storytelling and Interpretation

- Use short explanations that connect charts to stakeholder questions.
- Clearly label averages, counts, percentages and units.
- Label fixed notebook findings as full-dataset findings.
- Ensure descriptions remain accurate when filters change.
- Identify dashboard comparisons as unadjusted descriptive results.
- Distinguish them from the adjusted regression analyses in the hypothesis notebook.
- Avoid causal language and claims about percentage influence.
- Use the dashboard for exploration, not individual prediction or decisions about students.

## Data Limitations

- Retain the exam score of 101 consistently with the cleaned dataset and explain that its validity is uncertain.
- Include student counts in tooltips because small groups can produce unstable averages.
- Explain that filtering reduces the number of observations represented.
- Do not assume the dataset represents all students or schools.
- Explain that normalisation is a visual comparison method, not a measure of factor importance.

## Final Checks

- Confirm that each visual answers its planned stakeholder question.
- Check readability, colour contrast, spacing, legends and number formatting.
- Verify counts and averages against the cleaned dataset.
- Check that score bands cover every retained observation.
- Confirm that normalisation references remain fixed under filtering.
- Test slicers, factor selection, chart interactions, tooltips, navigation and reset buttons.
- Check empty selections and small groups.
- Confirm that any reshaped data does not inflate student counts.
- Ensure captions remain accurate under filtering.