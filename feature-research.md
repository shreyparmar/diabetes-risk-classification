# Feature-Research

## List of features in our dataset

1. Patient ID
2. Age
3. Gender
4. City
5. BMI
6. Family History Diabetes
7. Physical Activity
8. Diet type
9. Smoking status
10. Alcohol consumption
11. Hours sleep per night
12. Stress level
13. Fasting blood sugar
14. Hba1c level
15. Blood pressure (systolic)
16. Blood pressure (diastolic)
17. Waist circumference
18. Income bracket

**Label:** Diabetes risk

### 1. Patient ID

A unique identification number assigned & has no biological significance

### 2. Age

#### What is it?

Age is the person's age, usually recorded in completed years at the time of data collection.

#### What does it measure?

It captures life-stage and the gradual accumulation of genetic, metabolic, and lifestyle factors that can influence diabetes risk.

#### Relationship with diabetes

Older age is a recognized risk factor for prediabetes and type 2 diabetes. CDC lists age 45 or older among the major risk factors, although diabetes can occur at younger ages. [web:17][web:18]

#### Things to be careful about

- Confirm that age was measured before the diabetes-risk label to prevent leakage.
- Check for impossible values and decide how to handle very young or very old observations.
- Treat age as continuous unless there is a strong reason to create clinically meaningful bands.

#### Sources

- [CDC: Risk Factors](https://www.cdc.gov/diabetes/risk-factors/index.html) [web:17]

### 3. Gender

#### What is it?

Gender is a self-reported or recorded demographic variable. It should not automatically be treated as identical to biological sex.

#### What does it measure?

It may capture differences in biology, social conditions, healthcare access, pregnancy-related history, and lifestyle patterns. These pathways are context-dependent.

#### Relationship with diabetes

Gender alone is not a diagnosis or a universal rule for diabetes risk. Its predictive value depends on the population and may partly reflect other variables, such as pregnancy or gestational-diabetes history, which are not present in this dataset.

#### Things to be careful about

- Document the dataset's exact categories and coding.
- Do not infer gender from names or force nonbinary responses into arbitrary categories.
- Check subgroup performance and fairness; a model can be accurate overall while performing differently across groups.
- Avoid interpreting an association as a biological cause.

#### Sources

- [CDC: Type 2 Diabetes](https://www.cdc.gov/diabetes/about/about-type-2-diabetes.html) [web:18]

### 4. City

#### What is it?

City is a geographic or residential-location feature.

#### What does it measure?

It can act as a proxy for environmental, socioeconomic, healthcare-access, dietary, occupational, and urban-design differences. It is not a direct physiological measure.

#### Relationship with diabetes

A city's association with diabetes risk is population-specific. Location may correlate with risk through income, food availability, transport, pollution, healthcare access, and cultural patterns, but the feature does not establish that the city causes diabetes.

#### Things to be careful about

- City can create privacy and fairness risks, especially when the dataset has few observations per location.
- Rare cities and spelling variants need consistent handling.
- Avoid one-hot encoding locations with tiny sample sizes without validation safeguards.
- Check whether city is a proxy for protected characteristics or socioeconomic status.
- If the model will be deployed elsewhere, city categories may be missing or have different meanings; consider broader geographic features.

#### Sources

- [WHO: Diabetes](https://www.who.int/news-room/fact-sheets/detail/diabetes) [web:45]

### 5. BMI

#### What is it?

Body mass index (BMI) is calculated as weight in kilograms divided by height in metres squared. It is a screening measure and not a direct measurement of body fat. [web:9][web:14]

#### What does it measure?

BMI describes weight relative to height and serves as a proxy for overall body size and excess weight.

#### Relationship with diabetes

Higher BMI is associated with greater type 2 diabetes risk. However, risk also depends on age, family history, physical activity, ethnicity, and other factors. Asian populations may develop metabolic complications at lower BMI values than standard categories suggest. [web:2][web:3][web:5]

#### Relevant ranges / categories

| BMI (kg/m²) | Adult category |
|---|---|
| Below 18.5 | Underweight |
| 18.5–24.9 | Healthy weight |
| 25.0–29.9 | Overweight |
| 30.0–34.9 | Class 1 obesity |
| 35.0–39.9 | Class 2 obesity |
| 40.0 or higher | Class 3 obesity |

These are commonly used adult categories. Asian-specific diabetes-screening thresholds may be lower; NIDDK identifies BMI 23 or higher for Asian Americans as a risk threshold. [web:7][web:3]

#### Things to be careful about

- BMI does not distinguish fat from muscle or show fat distribution.
- Check height and weight units, missing values, and implausible measurements.
- Do not use BMI as a diagnosis.
- Waist circumference can add information about central adiposity.

#### Sources

- [CDC: About BMI](https://www.cdc.gov/bmi/about/index.html) [web:9]
- [CDC: Adult BMI Categories](https://www.cdc.gov/bmi/adult-calculator/index.html) [web:7]
- [NIDDK: Diabetes Risk Factors](https://www.niddk.nih.gov/health-information/diabetes/overview/risk-factors-type-2-diabetes) [web:3]

### 6. Family History Diabetes

#### What is it?

This feature records whether the person has a family history of diabetes, ideally specifying the affected relative and diabetes type.

#### What does it measure?

It captures inherited susceptibility and shared household, dietary, environmental, and behavioral influences.

#### Relationship with diabetes

Having a parent or sibling with type 2 diabetes is a recognized risk factor. [web:17][web:18]

#### Things to be careful about

- Distinguish first-degree relatives from more distant relatives.
- Separate type 1, type 2, gestational, and unknown diabetes where possible.
- Self-reported family history can be incomplete or inaccurate.
- Encode unknown separately from “no,” because missing knowledge is not evidence of no family history.

#### Sources

- [CDC: Risk Factors](https://www.cdc.gov/diabetes/risk-factors/index.html) [web:17]

### 7. Physical Activity

#### What is it?

Physical activity describes movement or exercise, often recorded as frequency, duration, intensity, or activity category.

#### What does it measure?

It estimates energy expenditure and sedentary or active behavior. A single categorical answer may not capture the full pattern.

#### Relationship with diabetes

Physical inactivity is a recognized type 2 diabetes risk factor. WHO recommends adults undertake 150–300 minutes of moderate aerobic activity or 75–150 minutes of vigorous activity weekly, with muscle strengthening also beneficial. [web:17][web:56]

#### Relevant ranges / categories

If the dataset uses categories, document their exact meanings. A useful representation can include inactive, insufficiently active, and meeting activity guidelines, provided the underlying questions support those categories.

#### Things to be careful about

- Self-reported activity is vulnerable to recall and social-desirability bias.
- Specify the time window, intensity, and whether occupational activity is included.
- Do not assume “exercise” captures sitting time or daily movement.
- Avoid turning a coarse category into precise minutes that were never measured.

#### Sources

- [WHO: Physical Activity](https://www.who.int/news-room/fact-sheets/detail/physical-activity) [web:58]
- [CDC: Risk Factors](https://www.cdc.gov/diabetes/risk-factors/index.html) [web:17]

### 8. Diet type

#### What is it?

Diet type is a broad classification of eating pattern, such as vegetarian, non-vegetarian, vegan, or another category defined by the dataset.

#### What does it measure?

It provides a coarse description of food preferences or restrictions. It does not directly measure calorie intake, food quality, carbohydrate quantity, fiber, or added sugar.

#### Relationship with diabetes

Diet patterns can influence body weight, insulin sensitivity, and cardiometabolic health. WHO recommends diets rich in fruits, vegetables, legumes, nuts, and whole grains, while limiting free sugars, saturated fats, and excess salt. [web:53][web:57]

#### Things to be careful about

- A diet label alone is too broad to determine whether a diet is healthy.
- Two people in the same category may consume very different foods.
- Record portion size, frequency, sugary drinks, refined carbohydrates, and fiber if available.
- Avoid assuming vegetarian or vegan automatically means low diabetes risk.
- Category definitions may be culturally specific and should be documented.

#### Sources

- [WHO: Healthy Diet](https://www.who.int/news-room/fact-sheets/detail/healthy-diet) [web:57]

### 9. Smoking status

#### What is it?

Smoking status records whether a person currently smokes, formerly smoked, or has never smoked. It should ideally include tobacco type and exposure amount.

#### What does it measure?

It captures tobacco exposure, a modifiable behavioral and health-risk factor.

#### Relationship with diabetes

Smoking is associated with increased type 2 diabetes risk and also increases cardiovascular risk. Tobacco avoidance is recommended as part of type 2 diabetes prevention. [web:45][web:59]

#### Relevant ranges / categories

Use categories such as never, former, and current smoker if the data support them. Pack-years or cigarettes per day can provide more information than a simple status.

#### Things to be careful about

- Clarify whether vaping, smokeless tobacco, and secondhand exposure are included.
- Former-smoker status needs a quit date or duration where possible.
- Self-report may understate exposure.
- Do not interpret smoking as a deterministic cause for an individual prediction.

#### Sources

- [WHO: Diabetes](https://www.who.int/news-room/fact-sheets/detail/diabetes) [web:45]
- [Cleveland Clinic: Smoking and Diabetes](https://health.clevelandclinic.org/smoking-and-diabetes) [web:59]

### 10. Alcohol consumption

#### What is it?

Alcohol consumption records drinking frequency, quantity, or a category such as none, occasional, or regular use.

#### What does it measure?

It estimates alcohol exposure, but a frequency-only field may miss drink size, binge episodes, and beverage strength.

#### Relationship with diabetes

The relationship can vary with amount, pattern of drinking, body weight, diet, liver health, and other factors. Alcohol can also affect glucose management and interact with diabetes medicines, so this feature should not be treated as a simple linear risk factor.

#### Things to be careful about

- Record standard drinks rather than only “yes/no” when possible.
- Separate abstainers, occasional use, moderate use, and heavy or binge use if sample size permits.
- Be sensitive to underreporting and cultural differences in reporting.
- Avoid assuming that any single drinking pattern is protective for every person.

#### Sources

- [WHO: Everyday actions for better health](https://www.who.int/europe/news-room/fact-sheets/item/everyday-actions-for-better-health-WHO-recommendations) [web:56]
- [Mayo Clinic: Diabetes care](https://www.mayoclinic.org/diseases-conditions/diabetes/in-depth/diabetes-management/art-20045803) [web:49]

### 11. Hours sleep per night

#### What is it?

This is the reported or measured average number of hours slept per night.

#### What does it measure?

It measures sleep duration, not necessarily sleep quality, regularity, insomnia, or sleep apnea.

#### Relationship with diabetes

Short sleep duration, particularly below seven hours in adults, is associated with a greater likelihood of diabetes along with obesity and high blood pressure. [web:50]

#### Relevant ranges / categories

For many adult analyses, less than 7 hours can be treated as short sleep, while approximately 7–9 hours is often used as a typical adult target range. These bands should be documented as analytical choices, not diagnostic categories.

#### Things to be careful about

- Self-reported hours may differ from actual sleep time.
- Ask about shift work, irregular schedules, sleep quality, and sleep disorders if possible.
- A single average may hide weekday–weekend variation.
- Do not interpret sleep duration alone as proof of diabetes risk.

#### Sources

- [CDC MMWR: Sleep Duration](https://www.cdc.gov/mmwr/volumes/65/wr/mm6506a1.htm) [web:50]

### 12. Stress level

#### What is it?

Stress level is a subjective or survey-based estimate of perceived psychological stress.

#### What does it measure?

It measures perceived strain rather than a directly observable biological quantity. Its meaning depends heavily on the questionnaire, scale, and time window.

#### Relationship with diabetes

Stress may be associated with diabetes risk indirectly through sleep, physical activity, diet, medication adherence, and stress-related hormonal responses. The association is complex and does not mean stress alone causes diabetes.

#### Things to be careful about

- Record the scale, wording, reference period, and whether a validated instrument was used.
- Treat “unknown” separately from low stress.
- Responses can vary by culture, language, and current circumstances.
- Avoid clinical interpretation of a survey score without appropriate validation.

#### Sources

- [NIDDK: Healthy Living with Diabetes](https://www.niddk.nih.gov/health-information/diabetes/overview/healthy-living-with-diabetes) [web:27]

### 13. Fasting blood sugar

#### What is it?

Fasting blood sugar, or fasting plasma glucose, is the blood glucose concentration measured after an appropriate fasting period, commonly at least eight hours.

#### What does it measure?

It measures glucose regulation at a fasting state and is used to screen for and help diagnose prediabetes and diabetes.

#### Relationship with diabetes

Elevated fasting glucose directly reflects impaired glucose regulation and is therefore one of the most informative features in this dataset. It may also be closely related to the diabetes-risk label, so possible label leakage must be considered.

#### Relevant ranges / categories

| Fasting plasma glucose | Interpretation |
|---|---|
| Below 100 mg/dL (5.6 mmol/L) | Normal |
| 100–125 mg/dL (5.6–6.9 mmol/L) | Prediabetes range |
| 126 mg/dL or higher (7.0 mmol/L or higher) | Diabetes range |

A diagnosis generally requires appropriate clinical confirmation rather than one isolated value. [web:31][web:32]

#### Things to be careful about

- Verify fasting duration, units, measurement method, and timing relative to the label.
- Acute illness, stress, medication, and laboratory variation can affect glucose.
- Do not call one measurement a diagnosis.
- If the label was created from glucose thresholds, including this feature may create direct or near-direct label leakage.

#### Sources

- [CDC: Diabetes Testing](https://www.cdc.gov/diabetes/diabetes-testing/index.html) [web:31]
- [NIDDK: Diabetes and Prediabetes Tests](https://www.niddk.nih.gov/health-information/professionals/clinical-tools-patient-management/diabetes/diabetes-prediabetes) [web:32]

### 14. Hba1c level

#### What is it?

HbA1c, or glycated hemoglobin, is the percentage of hemoglobin with glucose attached to it. It estimates average blood glucose over roughly the previous two to three months.

#### What does it measure?

It reflects longer-term glycemic exposure and does not require fasting. It is used for screening, diagnosis, and monitoring, subject to clinical limitations.

#### Relationship with diabetes

Higher HbA1c indicates poorer average glucose control and is strongly related to prediabetes and diabetes classification. Like fasting glucose, it may be extremely predictive or directly define the label, creating possible leakage.

#### Relevant ranges / categories

| HbA1c | Interpretation |
|---|---|
| Below 5.7% | Normal range |
| 5.7–6.4% | Prediabetes range |
| 6.5% or higher | Diabetes range |

Clinical diagnosis may require confirmation and consideration of the testing context. [web:34][web:35]

#### Things to be careful about

- Anemia, hemoglobin variants, kidney disease, pregnancy, and other conditions can affect HbA1c accuracy.
- Confirm that the assay is standardized and the units are percentages.
- Check whether HbA1c was measured before the outcome was assigned.
- If the label is based on HbA1c, exclude it for a model intended to predict risk before testing; otherwise the model may merely reproduce the rule used to create the label.

#### Sources

- [NIDDK: The A1C Test and Diabetes](https://www.niddk.nih.gov/health-information/diagnostic-tests/a1c-test) [web:34]
- [NIDDK: Recommended Tests for Prediabetes](https://www.niddk.nih.gov/health-information/professionals/clinical-tools-patient-management/diabetes/game-plan-preventing-type-2-diabetes/prediabetes-screening-how-why/recommended-tests-identifying-prediabetes) [web:35]

### 15. Blood pressure (systolic)

#### What is it?

Systolic blood pressure is the top number in a blood-pressure reading and represents arterial pressure during heart contraction.

#### What does it measure?

It measures one component of blood pressure and is usually recorded in mm Hg.

#### Relationship with diabetes

High blood pressure commonly coexists with metabolic risk and is recognized as a type 2 diabetes risk factor. It may reflect shared mechanisms such as insulin resistance, obesity, and vascular dysfunction, but it is not a diabetes diagnosis. [web:23]

#### Relevant ranges / categories

| Systolic reading | Category, when considered with diastolic pressure |
|---|---|
| Below 120 mm Hg | Normal |
| 120–129 mm Hg | Elevated, if diastolic is below 80 |
| 130–139 mm Hg | Stage 1 hypertension range |
| 140 mm Hg or higher | Stage 2 hypertension range |
| Above 180 mm Hg | Severe range requiring prompt attention, especially with symptoms |

Categories are based on the overall reading and should not be assigned from systolic pressure alone when diastolic information is available. [web:43]

#### Things to be careful about

- Use repeated, properly measured readings rather than a single reading where possible.
- Record medication use, measurement position, cuff size, and device validation if available.
- Avoid imputing the diastolic category from systolic alone.
- Check units and extreme values.

#### Sources

- [American Heart Association: Blood Pressure Explained](https://www.heart.org/en/health-topics/high-blood-pressure/blood-pressure-explained) [web:43]
- [CDC: Preventing Type 2 Diabetes](https://www.cdc.gov/diabetes/prevention-type-2/index.html) [web:23]

### 16. Blood pressure (diastolic)

#### What is it?

Diastolic blood pressure is the bottom number and represents arterial pressure between heartbeats.

#### What does it measure?

It measures the second component of a blood-pressure reading, in mm Hg.

#### Relationship with diabetes

Elevated blood pressure is associated with higher cardiometabolic risk and is a recognized risk factor for prediabetes and type 2 diabetes. [web:23]

#### Relevant ranges / categories

| Diastolic reading | Category, when considered with systolic pressure |
|---|---|
| Below 80 mm Hg | Normal or, with systolic 120–129, elevated |
| 80–89 mm Hg | Stage 1 hypertension range |
| 90 mm Hg or higher | Stage 2 hypertension range |
| Above 120 mm Hg | Severe range requiring urgent attention |

The final blood-pressure category is determined using both numbers, with the higher category generally controlling. [web:43]

#### Things to be careful about

- Diastolic pressure is not interchangeable with systolic pressure.
- Use repeated measurements and document measurement conditions.
- Consider antihypertensive treatment status where available.
- Check for impossible or clinically implausible values.

#### Sources

- [American Heart Association: Blood Pressure Explained](https://www.heart.org/en/health-topics/high-blood-pressure/blood-pressure-explained) [web:43]

### 17. Waist circumference

#### What is it?

Waist circumference is a tape-measured estimate of abdominal size, usually recorded in centimetres or inches.

#### What does it measure?

It is a practical proxy for central or abdominal adiposity, which BMI does not capture.

#### Relationship with diabetes

Larger waist circumference is associated with higher type 2 diabetes risk. CDC identifies measurements above 35 inches for women and above 40 inches for men as higher-risk thresholds in its healthy-weight guidance. [web:33]

#### Relevant ranges / categories

| Measurement | Common higher-risk threshold |
|---|---|
| Women | More than 35 inches (about 88 cm) |
| Men | More than 40 inches (about 102 cm) |

Thresholds can vary by ethnicity, clinical guideline, and measurement protocol, so the dataset's population should be considered.

#### Things to be careful about

- Specify the anatomical measurement site and units.
- Clothing, breathing phase, posture, and tape placement affect results.
- Do not treat waist circumference as interchangeable with BMI.
- Consider ethnic-specific thresholds where scientifically justified.
- Avoid collecting or exposing this measurement unnecessarily because it is health information.

#### Sources

- [CDC: Healthy Weight and Diabetes](https://www.cdc.gov/diabetes/living-with/healthy-weight.html) [web:33]
- [Research on BMI, waist circumference, and type 2 diabetes](https://pmc.ncbi.nlm.nih.gov/articles/PMC2905837/) [web:37]

### 18. Income bracket

#### What is it?

Income bracket is a grouped estimate of individual or household income.

#### What does it measure?

It is a socioeconomic indicator that may correlate with food access, healthcare access, housing, education, work conditions, and opportunities for physical activity.

#### Relationship with diabetes

Income is not a biological cause of diabetes, but socioeconomic conditions can shape exposure to diabetes risk factors and access to prevention and treatment. The direction and strength of the relationship vary by country, city, age, and measurement method.

#### Things to be careful about

- Document whether income is individual or household income and the reference year.
- Adjust for household size, inflation, and local cost of living when appropriate.
- Treat “prefer not to say” and missing responses separately from the lowest bracket.
- Income is sensitive personal information; minimize collection, protect it, and assess whether it is appropriate for deployment.
- Check whether the model reinforces unequal access or acts as a proxy for protected characteristics.

#### Sources

- [WHO: Diabetes](https://www.who.int/news-room/fact-sheets/detail/diabetes) [web:45]
- [WHO: Healthy Diet](https://www.who.int/news-room/fact-sheets/detail/healthy-diet) [web:57]
