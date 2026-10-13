# Student Performance Analysis — Detailed Project Roadmap

*Roadmap reference date: 6 October 2026. This roadmap will describe the intended project workflow in future tense. It will serve as a reconstructed planning document, not as evidence that this document existed before development. Dated GitHub issues and commits will provide the historical record of the work.*

## Purpose and scope

I will investigate how study habits, attendance, educational resources and other recorded student characteristics relate to exam performance. I will combine data preparation, exploratory analysis, three statistical hypothesis tests, one linear regression prediction model and an interactive Power BI report.

I will write for education stakeholders and non-technical readers while providing enough detail for a technical reader to inspect and reproduce the analysis. I will distinguish descriptive patterns, adjusted statistical associations and predictive model importance throughout the project.

I will use the Student Performance Factors dataset from Kaggle. I will check the publisher's documentation and explain any uncertainty about data collection, generation, sampling and representativeness. I will avoid presenting the analysis as a validated system for making decisions about individual students.

## How I will organise the work

I will use the following stages in dependency order. Each stage will represent a work block, not a claim about a particular calendar day. I will spread longer stages across several sessions and reserve time before submission for corrections.

| Stage | Work block | Planned output | Completion check |
| --- | --- | --- | --- |
| 1 | Requirements and questions | Scope and assessment checklist | I will map every requirement to evidence. |
| 2 | Repository and environment | Organised, reproducible workspace | I will check file structure and dependencies. |
| 3 | Dataset inspection | Data-quality audit and dictionary | I will account for all columns and quality issues. |
| 4 | Data preparation | Cleaned analytical dataset | I will verify and explain each transformation. |
| 5 | Exploratory analysis | Statistics, charts and initial findings | I will connect charts to research questions. |
| 6 | Hypothesis testing | H1–H3 models, tests and interpretation | I will check assumptions, uncertainty and sensitivity. |
| 7 | Predictive modelling | Linear regression and baseline evaluation | I will evaluate on held-out data without leakage. |
| 8 | Analytical exports | Consistent Power BI input files | I will reconcile exported values with notebook outputs. |
| 9 | Dashboard development | Four-page interactive report | I will test visuals, navigation and filters. |
| 10 | Documentation and reflection | README and supporting documents | I will check accuracy, evidence and accessibility. |
| 11 | Final validation | Recorded submission checks | I will run the workflow and resolve blocking problems. |
| 12 | Board review and submission | Final repository and submitted link | I will confirm the required deliverables and receipt. |

## 1. Requirements, audience and research questions

- I will read the assessment brief and submission instructions before deciding which deliverables will be necessary.
- I will separate assessed requirements from optional improvements and avoid adding work merely because a template mentions it.
- I will confirm the deadline, submission location and required access permissions.
- I will check whether a presentation, recording or live demonstration will be required. I will only plan one if the brief or tutor confirms it.
- I will define the intended audience and the questions the analysis will answer.
- I will translate these questions into GitHub issues with a user story, priority and measurable acceptance criteria.
- I will use To Do, In Progress and Done columns and link relevant issues to the repository.
- I will map requirements to notebooks, charts, dashboard pages and documentation so that evidence will be easy to find.

### Questions I will investigate

1. How will exam scores be distributed across the dataset?
2. Will attendance remain associated with exam scores after accounting for study hours and previous scores?
3. Will the association between tutoring and exam scores vary with previous performance?
4. Will resource-access groups differ after accounting for family income and previous scores?
5. How accurately will linear regression predict unseen exam scores compared with a mean baseline?
6. Which original predictors will the fitted model rely on most?
7. How will interactive exploration help readers investigate combinations of student characteristics?

**Stage output:** I will produce a clear scope, a requirements-to-evidence checklist and a prioritised project board.

## 2. Repository, folders and working environment

- I will maintain the project in the student-performance-analysis Git repository.
- I will keep the original dataset in `data/raw/` and derived datasets and exports in `data/processed/`.
- I will organise preparation, exploratory analysis, hypothesis testing and machine learning in separate notebooks under `jupyter_notebooks/`.
- I will store the report and design documentation under `powerbi/`.
- I will store exported charts and dashboard screenshots under `visualisations/`.
- I will document variables in `data_dictionary.md` and provide the main project guide in `README.md`.
- I will create a local virtual environment and select its Python kernel for the notebooks.
- I will record the dependencies needed to reproduce the work in `requirements.txt` and check that their versions can be installed together.
- I will exclude the virtual environment, caches, credentials and Windows `desktop.ini` files from Git.
- I will prefer portable relative paths and explain any Power BI source-path changes needed on another computer.
- I will make focused commits at meaningful milestones, inspect staged files and push regularly.

**Stage output:** I will establish an organised repository and a documented environment that another reader will be able to set up.

## 3. Dataset source, inspection and data dictionary

- I will record the dataset title, publisher and source link.
- I will inspect the publisher's definitions and distinguish documented information from assumptions.
- I will load the original CSV and check its shape, column names, data types and sample records.
- I will verify the expected 6,607 rows and 20 original variables against the actual file.
- I will count missing values by column and inspect whether apparent blanks or unusual strings will need treatment as missing.
- I will check exact duplicate rows and decide whether they represent errors or potentially valid repeated combinations of characteristics.
- I will inspect unique and distinct values, category labels and numerical ranges.
- I will check spelling, whitespace, inconsistent capitalisation and unexpected category values.
- I will investigate unusual values, including exam scores above a conventional 100-point scale, without assuming a grading scale the source does not establish.
- I will record which variables will be numerical, counts, binary categories, nominal categories or ordered categories.
- I will document units, category meanings, unavailable definitions and relevant limitations for all 20 columns.
- I will explain that sensitive attributes will require careful interpretation and will not justify stereotyping or discriminatory decisions.

**Stage output:** I will produce a data-quality audit and a complete dictionary before making analytical claims.

## 4. Data preparation and validation

- I will preserve the original CSV and make transformations in a reproducible preparation notebook.
- I will document the reason for each correction, imputation, removal or retained unusual value.
- I will choose missing-value treatment by variable type and analytical purpose rather than applying one rule automatically.
- I will distinguish descriptive-data preparation from predictive-model preprocessing.
- I will avoid learning imputation values, encodings or other fitted transformations from the full dataset before a predictive train/test split.
- I will avoid treating imputed target values as genuine observed exam outcomes in model evaluation. If target values are missing, I will document how affected records will be handled.
- I will standardise categories where needed while retaining their documented meanings.
- I will check missing counts, types, allowed categories, duplicate counts and numerical ranges after cleaning.
- I will reconcile the row count before and after preparation and explain any difference.
- I will save the cleaned analytical CSV and verify that it can be loaded successfully.
- I will record limitations introduced by cleaning and consider sensitivity checks where a choice could materially affect conclusions.

**Stage output:** I will create a validated analytical dataset with an auditable preparation process.

## 5. Exploratory data analysis

- I will calculate counts, means, medians, standard deviations, quartiles, ranges and other relevant descriptive statistics.
- I will inspect distinct numerical values so that chart choices will reflect the data's actual granularity.
- I will examine exam-score distribution using a histogram and discuss its concentration, spread and unusual values.
- I will explore study hours and exam scores with a scatter plot and fitted trend.
- I will examine attendance and previous scores in relation to exam performance.
- I will compare categorical groups using clearly labelled summaries and appropriate charts.
- I will consider group sizes alongside averages and avoid interpreting small-group differences as reliable evidence.
- I will calculate and visualise Pearson correlations for the numerical variables.
- I will explain that correlation will summarise pairwise linear relationships and will not account for other predictors or establish causation.
- I will connect initial patterns to the questions for adjusted hypothesis testing.
- I will give every retained chart a clear title, readable labels and a short interpretation.
- I will export static images for the README and interactive HTML charts where they will add value.
- I will avoid accumulating charts that repeat the same point without helping the reader.

**Stage output:** I will create a focused exploratory notebook and supporting visualisations that will lead naturally into the statistical analysis.

## 6. Statistical hypothesis testing

### Shared approach

- I will state a null and alternative hypothesis for each question before interpreting results.
- I will explain why regression will suit questions requiring adjustment or an interaction.
- I will use a significance level of 0.05 and report coefficients, confidence intervals and p-values.
- I will use heteroskedasticity-robust HC3 standard errors where planned and explain that they will not correct every possible model problem.
- I will inspect model specification, residual patterns, Q–Q plots, multicollinearity where relevant and influential observations.
- I will use Cook's distance to identify observations for investigation and sensitivity analysis, rather than deleting them automatically.
- I will compare key estimates before and after justified sensitivity checks and report whether conclusions change.
- I will apply and document the planned Holm correction across the three primary hypothesis-test p-values. I will specify which p-value will represent each hypothesis.
- I will distinguish statistical significance, effect size and practical interpretation.
- I will describe a non-significant result as insufficient evidence against the null, not proof that no relationship exists.

### H1 — Attendance and exam performance

- I will fit a model of Exam_Score using Attendance, Hours_Studied and Previous_Scores.
- I will test whether the attendance coefficient will differ from zero, interpreting its direction in relation to the proposed positive association.
- I will translate the estimate into exam-score points per ten percentage points of attendance.
- I will create an adjusted prediction chart with uncertainty where appropriate.
- I will assess whether influential observations materially alter the attendance estimate.

### H2 — Tutoring and previous scores

- I will centre tutoring sessions and previous scores to make main effects easier to interpret.
- I will fit their main effects and interaction.
- I will use the interaction test as the primary test of whether the tutoring association will vary with previous performance.
- I will plot predicted scores across tutoring levels for selected previous-score values within the observed data.
- I will document the selected values consistently in the notebook, exports, dashboard and README.
- I will distinguish the overall tutoring association from evidence about variation in that association.

### H3 — Access to resources

- I will model Access_to_Resources as a categorical predictor with Low access as the reference group.
- I will account for Family_Income and Previous_Scores and document how family income will be encoded.
- I will use a joint Wald test for the resource-access terms as the primary hypothesis test.
- I will report High-versus-Low and Medium-versus-Low adjusted differences with confidence intervals.
- I will label adjusted differences accurately rather than describing them as unadjusted group averages.
- I will explain that adjustment alone will not establish a causal effect of providing resources.

**Stage output:** I will produce three clearly specified tests, diagnostic evidence, sensitivity checks and interpretations consistent with the outputs.

## 7. Linear regression prediction model

- I will define Exam_Score as the prediction target and identify eligible predictors.
- I will justify linear regression as an interpretable baseline approach for a numerical outcome.
- I will separate this prediction task from the three explanatory hypothesis models.
- I will create a reproducible train/test split and record its proportions and random seed.
- I will check for information leakage, inappropriate identifiers and predictors that would not be available at prediction time.
- I will fit preprocessing on training data only, ideally within a pipeline that will also transform the held-out test data.
- I will document numerical and categorical preprocessing and handle previously unseen categories appropriately.
- I will fit a mean baseline using training-target information and fit the linear regression model.
- I will evaluate both models on the same held-out test records using MAE, RMSE and R².
- I will explain MAE and RMSE in exam-score points and R² as a measure of explained test-set variation relative to the test mean.
- I will inspect prediction errors and discuss why a low average error may coexist with some much larger errors.
- I will avoid repeatedly choosing changes based on test-set performance; any tuning will require validation within the training data.
- I will calculate permutation importance using decrease in test R² with 30 repeats and document its variability.
- I will evaluate the original predictor columns consistently through the fitted pipeline.
- I will explain that permutation importance will reflect reliance of this fitted model on a predictor, not a causal effect or a share that must sum to 100%.
- I will label dashboard importance multiplied by 100 as a decrease in test R² in percentage points.
- I will report limitations of one split, linear assumptions and uncertain population representativeness.

**Stage output:** I will provide a reproducible predictive pipeline, baseline comparison, error interpretation and predictor-importance chart.

## 8. Exporting analytical results for Power BI

- I will export the cleaned data and the statistical and modelling summaries needed by the report.
- I will use consistent column names, category ordering and numerical types.
- I will reshape numerical correlations into a format suitable for the Power BI matrix.
- I will export adjusted predictions or differences for H1–H3 and document their meaning.
- I will export model importance values with clear units.
- I will compare exported values with notebook results before building the dashboard.
- I will distinguish rounded display values from the underlying numerical values.
- I will document that imported statistical results will remain fixed unless the notebooks and exports are rerun.
- I will refresh dependent exports and the report together whenever the analysis changes.

**Stage output:** I will provide traceable input files whose figures will agree with the analytical notebooks.

## 9. Power BI dashboard planning and development

### Design and audience

- I will document the dashboard layout and the purpose of each visual in `powerbi/dashboard_plan.md`.
- I will use a consistent purple theme, readable text, clear spacing and concise finding panels.
- I will map each visual to an audience question and avoid using decoration in place of explanation.
- I will keep analytical details in supporting documentation while making the report understandable to non-technical readers.

### Page 1 — Overview

- I will display student count, average exam score, average attendance and average study hours.
- I will show average exam score by attendance alongside student counts.
- I will use ranked horizontal bars for model importance and a factor selector for choosing which predictors to display.
- I will provide relevant student-characteristic slicers.
- I will make clear that student slicers will explore records while the factor selector will control displayed importance bars; these controls will not retrain the model.

### Page 2 — Hypothesis Findings

- I will use H1, H2 and H3 bookmark buttons to switch between findings.
- I will show the attendance relationship, tutoring interaction and resource-access differences with appropriate charts.
- I will pair each chart with a short finding and the relevant qualification.
- I will check that the selected bookmark, displayed chart, titles and explanatory text agree.

### Page 3 — Explore Performance

- I will use a decomposition tree to explore average exam scores across combinations of student characteristics.
- I will explain that each branch will narrow the selected group.
- I will review available space and remove visuals that obscure the tree or repeat another page.
- I will note any shortened labels or missing subgroup counts that limit interpretation.

### Page 4 — Correlations

- I will display a seven-by-seven matrix of numerical-variable correlations.
- I will use conditional formatting centred on zero and show a consistent number of decimal places.
- I will disable meaningless totals.
- I will explain the direction and strength of correlations and distinguish them from adjusted regression estimates.

### Interaction checks

- I will test slicers individually and in combination.
- I will test all hypothesis bookmarks and selected-button styling.
- I will check factor selection and decomposition-tree expansion.
- I will confirm which visuals will filter, highlight or remain unchanged.
- I will check default views, empty selections, text clipping and readability.
- I will reconcile displayed values with the underlying exports.
- I will save the PBIX and capture clean screenshots with the intended page or bookmark active.

**Stage output:** I will deliver a four-page report with documented and tested interaction behaviour.

## 10. README, storytelling and learning reflection

- I will introduce the project through an audience question and explain its purpose and scope.
- I will document the source, dataset structure, data files and link to the dictionary.
- I will explain requirements, research questions and hypothesis results.
- I will describe preparation, exploratory analysis, statistical testing and prediction methods.
- I will connect the exam-score distribution, study-hours relationship, correlations, adjusted findings and model importance into a coherent story.
- I will report the baseline and linear-regression evaluation results in a readable table.
- I will explain each dashboard page, its controls and its interaction boundaries.
- I will include a folder-structure guide, dependencies, notebook run order and Power BI opening instructions.
- I will add a project-board link and an accurately labelled PBIX download link.
- I will explain that the downloaded report will be interactive in Power BI Desktop, rather than imply that GitHub will run it in a browser.
- I will use descriptive image filenames and confirm that H1, H2 and H3 screenshots match their sections.
- I will remove draft labels, repeated paragraphs and obsolete design descriptions.
- I will describe challenges, decisions, solutions and learning using specific examples.
- I will record fixed bugs separately from remaining limitations.
- I will acknowledge the dataset, external documentation, adapted code and AI assistance accurately.
- I will describe optional future work, including an optional Streamlit interface, without presenting it as a current requirement.
- I will link this roadmap as reconstructed workflow documentation; I will use issue and commit history for evidence of when work occurred.

**Stage output:** I will produce documentation that will help readers understand, inspect and run the project.

## 11. Final validation and corrections

- I will save working files and inspect Git status before final testing.
- I will restart notebook kernels and run notebooks in the documented dependency order.
- I will resolve execution errors and investigate warnings that affect results.
- I will check that documented paths and dependency instructions match the actual project.
- I will verify cleaned-data integrity and key export values after the final run.
- I will check that the hypothesis summary includes the planned primary tests and multiple-testing correction.
- I will refresh Power BI against the final exports and retest its essential interactions.
- I will verify that the final README screenshots and reported figures match the saved report and notebooks.
- I will inspect the GitHub-rendered README for broken images, links, formatting and filenames with incorrect case.
- I will test the project-board and dashboard links with the intended reader's access in mind.
- I will check that required deliverables will be committed and that credentials, caches and environment folders will be excluded.
- I will record the checks actually performed, their results and any unresolved issues.
- I will update the README's remaining-checks section only when the checks have genuinely been completed.

**Stage output:** I will retain a truthful validation record and resolve issues that would block reproducibility or assessment.

## 12. Project-board review and submission

- I will review each remaining issue against every acceptance criterion.
- I will link completed work or identify its location before marking an issue Done.
- I will leave incomplete work open and prioritise it according to submission impact.
- I will close unnecessary or out-of-scope tasks as Not planned rather than imply they were completed.
- I will confirm whether presentation work will be required from the actual submission instructions.
- I will check that issue status and board status agree.
- I will commit final changes with clear messages and push them to GitHub.
- I will confirm that the local branch will be up to date with its remote and that no required changes will remain untracked or uncommitted.
- I will compare the final repository against the assessment checklist.
- I will submit the correct repository link and any additional required files through the specified platform.
- I will retain the submission confirmation and avoid unrecorded changes to the submitted version.

**Stage output:** I will submit the required deliverables with an accurate board and a traceable final repository state.

## How I will manage changes and time

- At the beginning of each session, I will review the current board, Git status and the next dependency.
- I will select a manageable set of tasks and finish the current analytical question before expanding scope.
- I will divide long coding, dashboard and documentation tasks into smaller work blocks.
- I will allow breaks and leave clear progress notes so that work can resume without repeating completed steps.
- At each milestone, I will check outputs, make a focused commit and update the relevant issue.
- If results change, I will update affected exports, dashboard content and documentation together.
- If time becomes limited, I will prioritise correctness, reproducibility, required deliverables and final validation before optional styling or extra features.
- At the end of each session, I will record what has been completed, what remains uncertain and the exact next step.

