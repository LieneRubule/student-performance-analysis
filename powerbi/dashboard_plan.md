# Power BI Dashboard Plan

## Purpose and Audience

The dashboard will help teachers and education support staff explore student performance and factors associated with exam scores.

It will present descriptive findings from the cleaned dataset. Relationships will be described as associations, not evidence of cause and effect.

## Planned Pages and Layout

### Page 1 — Overview

- Top: page title and short introduction.
- Below the title: cards showing student count, average exam score, average attendance and average study hours.
- Centre left: column chart showing student counts by exam-score band.
- Centre right: bar chart showing student counts by school type.
- Bottom: brief findings and a data-limitations note.
- Filters: gender and school type.

### Page 2 — Attendance & Study

- Top: page title and filters.
- Centre left: scatter plot of attendance versus exam score.
- Centre right: line chart of average exam score by ordered study-hour group.
- Bottom: explanations of the main patterns.
- Filters: gender, attendance and study hours.
- Tooltips: relevant values and group counts for aggregated results.

### Page 3 — Resources & Support

- Top: page title and filters.
- Centre left: bar chart of average exam score by resource-access level.
- Centre right: column chart of average exam score by tutoring-session count.
- Bottom: explanations, including a warning about small tutoring groups.
- Filters: family income and resource access.
- Tooltips: average exam score and student count for each group.

## Stakeholder Questions and Planned Visuals

| Stakeholder question | Planned visual | Page |
|---|---|---|
| How many students are represented, and what are the overall averages? | Summary cards | Overview |
| How are exam scores distributed? | Student counts by exam-score band | Overview |
| What is the school-type composition of the dataset? | Student counts by school type | Overview |
| How does attendance relate to exam performance? | Attendance versus exam score scatter plot | Attendance & Study |
| How do average scores vary across study-hour groups? | Line chart of grouped averages | Attendance & Study |
| How do average scores differ by resource access? | Bar chart of group averages | Resources & Support |
| How do average scores vary with tutoring sessions? | Column chart with group counts in tooltips | Resources & Support |

## Colours, Text and Navigation

- Use a light background, dark text, and consistent purple and teal chart colours.
- Use clear titles, readable fonts and labelled axes with units.
- Support colour with text labels so meaning does not depend on colour alone.
- Use the page names Overview, Attendance & Study, and Resources & Support for navigation.
- Keep titles, filters and explanations in consistent positions.
- Clearly identify averages, counts and active filters.

## Main Design Decisions

- Start with an overview before presenting detailed relationships.
- Limit each page to two main charts to keep the layout readable.
- Use a scatter plot to show the spread of individual observations.
- Use ordered study-hour groups to make average patterns easier to read. These groups are not a time series.
- Use bars and columns for category comparisons, with value axes starting at zero.
- Order resource access as Low, Medium and High.
- Show group counts alongside averages through tooltips, because small groups can produce unstable averages.
- Retain the exam score of 101 consistently with the cleaned dataset and explain its uncertain validity in the limitations.
- Label dashboard comparisons as unadjusted descriptive results. They are different from the adjusted regression results in the hypothesis-testing notebook.
- Note that filters change the displayed sample; notebook hypothesis results refer to the full analysed dataset.