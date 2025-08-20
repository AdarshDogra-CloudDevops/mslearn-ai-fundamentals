# Lesson 14: Exploring Datasets to Define a Predictive Problem

## Lesson Description

In this lesson, students will act as sports data analysts to explore three datasets in **Azure ML Designer**:

- Clemson Football  
- South Carolina Basketball  
- Gamecocks Baseball  

Working in teams, students will examine relationships in the data, choose one dataset to focus on, and define the modeling problem they want to solve for their final project (e.g., "Find the next great quarterback"). Students will identify appropriate features and propose whether to use **classification** or **regression** based on their label.

---

## Main Learning Goal

Students will use **data exploration techniques** to identify patterns in real-world sports data, define a **machine learning problem**, and select the **appropriate modeling method**.

---

## Essential Question

**How can we use sports data and machine learning to predict which players will become the next top performers?**

---

## Standards

- **AP6.2**: Design, build, and test level-appropriate algorithms that use linear regression and describe existing outliers in the context of the programming solution.

---

## Objectives

- Identify key patterns and relationships in real sports datasets using **Azure ML Designer**.
- Select one dataset to model and define a **specific prediction task** (e.g., predicting top performers).
- Choose an appropriate machine learning technique (**linear regression** or **classification**) to support their modeling goal.

---

## Dataset Discovery Goal

You will independently explore **three datasets** and identify how the data can be used to solve a predictive problem. Using prior knowledge of **features, labels,** and **model types**, you will propose a target (label) before the teacher confirms the intended modeling direction.

---

## Dataset Previews – Individual Exploration

### General Instructions

Each dataset preview includes:

- A complete list of **columns**
- 5 sample **player rows**
- No **label column** highlighted

You are tasked to:

- Scan feature names  
- Ask: “What kind of player performance could this data help me predict?”  
- Look for patterns or useful variables  
- Identify which features seem most important  

---

### Dataset 1: Clemson Football – Offensive and Defensive Performance

**Filename**: `Football_Dataset.csv`

#### Description

- Player-level stats from Clemson University Football team (2024 season)
- Covers offensive & defensive roles

#### Key Features (Columns)

| Column | Description |
|--------|-------------|
| Player | Player name (text) |
| Pos | Player’s position (e.g., QB, RB, WR) |
| G | Games played |
| Rush_Yds | Rushing yards |
| Rec_Yds | Receiving yards |
| TDs | Total touchdowns |
| Comb_Tackles | Total tackles |
| Sacks | Total sacks |
| INT | Interceptions |
| Passing_Yds | Passing yards |
| Passing_TDs | Passing touchdowns |
| All_Purpose_Yds | Total offensive yards |
| Total_Points | Total points scored |

> Note: Binary labels (`is_qb1`, `is_lockdown_defender`) are hidden initially.

#### Exploration Focus

- Which stats reflect offensive or defensive excellence?
- Can positions be inferred from stats?
- How would you define a “breakout” player?

#### Reflection Prompts

- Could this data predict strong offensive/defensive players?
- What defines useful performance indicators?
- Can stats alone suggest positions?

---

### Dataset 2: Baseball Batting – Multi-Year Hitting Performance

**Filename**: `Batting_Dataset.csv`

#### Description

- South Carolina Baseball team stats over 2022–2024
- Offensive performance: contact, power, consistency

#### Key Features (Columns)

- `AVG_2022–2024`: Batting averages
- `HR_2022–2024`: Home runs
- `OPS_2022–2024`: On-base + slugging %
- `SLG%_2022–2024`: Slugging %
- `OB%_2022–2024`: On-base %
- `RBI_2022–2024`: Runs batted in
- `BB_2022–2024`: Walks
- `K_2022–2024`: Strikeouts
- `H_2022–2024`: Hits
- `2B_2022`, `3B_2022`: Extra-base hits
- `GP_2022–2024`: Games played
- `AB_2022–2024`: At-bats

#### Exploration Focus

- What defines hitting success?
- Use prior years to predict 2024?
- Choose classification or regression?

#### Reflection Prompts

- What makes a strong or power hitter?
- Which stats from 2022–2023 best predict 2024?
- Use one stat or combination?

---

### Dataset 3: Baseball Pitching – Multi-Year Pitcher Performance

**Filename**: `Pitching_Dataset.csv`

#### Description

- Pitcher-level stats from 2022–2024 seasons
- Covers effectiveness, control, dominance

#### Key Features (Columns)

- `GP_2022–2024`: Games played
- `APP_2022–2024`: Appearances
- `GS_2022–2024`: Games started
- `ERA_2022–2024`: Earned run average
- `WHIP_2022–2024`: Walks + Hits per Inning Pitched
- `K_2022–2024`: Strikeouts
- `BB_2022–2024`: Walks allowed
- `H_2022–2024`: Hits allowed
- `HR_2022–2024`: HRs allowed
- `WIN_2022–2024`: Wins
- `LOSS_2022–2024`: Losses
- `B/AVG_2022–2024`: Opponent batting average
- `WP_2022–2024`: Wild pitches

#### Exploration Focus

- What makes a pitcher an “ace”?
- How do stats reflect improvement?
- What stats best predict success?

#### Reflection Prompts

- What pitching stats define performance?
- Use ERA alone or with others?
- Choose classification or regression?

---

## Initial Reflection Questions (SREB_U5_L14_Handout)

1. What dataset did you choose? (Football, Batting, Pitching)  
2. How many players (rows) are in your dataset?  
3. Which stats or features stand out to you?  
4. What label (target) do you think would be interesting to predict?  
5. Would this be a classification or regression model? Why?  

---

## Key Takeaways

- There are **multiple valid ways** to frame a prediction problem.
- Labels can be **custom-created** or **predefined**, but both require understanding of features.
- Labels reflect real-world roles — like being named a starter or standout player.

---

## Dataset Deep Dive and Modeling Plan

### Setup Instructions

1. Open the chosen CSV file in **Excel, Google Sheets, or Azure**.
2. Review the structure and patterns.

**Available Files**:
- `Clemson_Football_Dataset.csv`
- `Batting_Dataset__Slugger_Balanced_.csv`
- `Pitching_Dataset.csv`

---

### Data Exploration Tasks

#### A. Structural Analysis

- How many **rows (players)** are in the dataset?
- How many **columns**?
- Any **missing/zero-filled** values?
- Types of values: numerical, categorical, binary?

#### B. Identify a Target (Label)

- Choose a prediction target:
  - **Classification**: `slugger`, `ace_pitcher`, `is_qb1`
  - **Regression**: `HR_2024`, `OPS_2024`, `ERA_2024`

#### C. Select Features

- Choose **5–8 input features**
- Use past data to inform prediction
- Avoid using columns **too similar to the label**

#### D. Classification or Regression?

- Is the label categorical or numeric?
- What **question** does your model answer?

---

### Handout Questions (SREB_U5_L14_Handout)

1. Dataset selected  
2. Prediction goal (e.g., predict ERA_2024)  
3. Label column  
4. Model type (classification or regression)  
5. Features selected (at least 5)  
6. Why did you choose those features?

---

## Outcome

By the end of this lesson, students will:

- Understand the structure of their chosen dataset  
- Identify a suitable **label** and **features**  
- Decide between **classification or regression**  
- Be prepared to load the dataset into Azure ML Designer (for Lesson 15)

---

## Gallery Walk

### Objective

Present and refine your modeling plan through peer feedback.

### What to Present

Each student shares:

- Chosen dataset (Football, Batting, Pitching)  
- Label column  
- 5–8 selected feature columns  
- Model type (classification or regression)  
- 1-sentence summary of the predictive question

### Peer Feedback Prompts

- **What’s strong about this plan?**  
- **What might they need to clarify?**  
- **What else could they try?**

> Leave feedback on at least **3 peers’ plans**.

---

## Exit Ticket (SREB_U5_L14_Handout – Page 2)

1. What dataset are you working on?  
2. What is your label, and why did you choose it?  
3. What are you most confident about in your plan?
4. Q4: What are you still unsure about?