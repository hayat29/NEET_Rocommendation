# Personalized Student Recommendations for NEET Preparation

---

## Overview <a name="overview"></a>
This Python-based solution analyzes quiz performance data to provide **personalized recommendations** for students preparing for the NEET (National Eligibility cum Entrance Test). The system:
- Identifies weak areas and improvement trends.
- Suggests topics, difficulty levels, and study strategies.
- Predicts NEET ranks using machine learning models.

Built for the [NEET Testline App](https://play.google.com/store/apps/details?id=com.testline.neet), it leverages two datasets:
1. **Current Quiz Data**: Recent quiz submissions with questions, topics, and responses.
2. **Historical Quiz Data**: Performance from the last 5 quizzes (scores, response maps).

---

## Key Features <a name="key-features"></a>
1. **Performance Analysis**  
   - Topic-wise accuracy breakdown.
   - Difficulty-level performance (Easy/Medium/Hard).
   - Time management insights (average time per question).

2. **Personalized Recommendations**  
   - Focus areas based on weak topics.
   - Study plans tailored to difficulty levels.
   - Practice strategies (e.g., "Revise cell biology diagrams").

3. **NEET Rank Prediction**  
   - Predicts ranks using regression models (Linear Regression, Random Forest).
   - Model accuracy: **MSE = 80,439**, R² = **0.76**.

4. **Visual Analytics**  
   - Interactive charts for topic/difficulty distribution.
   - Progress tracking over historical quizzes.

---

## Setup Instructions <a name="setup-instructions"></a>

### Prerequisites
- Python 3.8+
- Jupyter Notebook (optional)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/hayat29/NEET-recommendations.git
   cd neet-recommendations


  ---

  Install dependencies:
  pip install -r requirements.txt


  ---

 Run the Jupyter Notebook:
 jupyter notebook neet_recommendation.ipynb

 ---

 Create a static folder for outputs:
 mkdir static

 ---

 Project Structure 

 neet-recommendations/
├── data/                    # Sample datasets (optional)
├── static/                  # Outputs: Visualizations, models, results
│   ├── topic_distribution.png
│   ├── difficulty_analysis.png
│   ├── neet_model.pkl
│   └── analysis_results.json
├── neet_recommendation.ipynb # Main Jupyter Notebook
├── requirements.txt         # Dependency list
└── README.md                # This file

---

Approach 
1. Data Collection & Cleaning
APIs Used:

Current Quiz: https://www.jsonkeeper.com/b/LLQT

Historical Data: https://api.jsonserve.com/rJvd7g

Steps:

Normalize nested JSON structures.

Handle missing values (e.g., difficulty_level).

Derive metrics: avg_time_per_question, accuracy_rate.

2. Exploratory Data Analysis (EDA)
Question Analysis:

Distribution by topic and difficulty.

Subject categorization (Biology/Chemistry/Physics).

Student Performance:

Accuracy vs. time spent.

Historical progress trends.

3. Recommendation Engine
Difficulty Index:

questions_data['difficulty_index'] = (
    (description_length * 0.4) + 
    (missing_solution_penalty * 0.3) + 
    (visual_aid_complexity * 0.3)
)

Study Plans:

Difficulty	Study Time	Strategy
Easy	1 hour	Quick revision of NCERT diagrams
Hard	3 hours	Solve 10+ PYQs on genetics


4. Model Training
Features: average_score, topic_mastery, hard_question_accuracy.

Algorithms Tested:

Linear Regression (Baseline)

Random Forest (Best performance: MSE = 49,260,360)

Support Vector Regressor

Schema:

json
Copy
{
  "id": "quiz_43",
  "topic": "Structural Organisation in Animals",
  "questions": [
    {
      "id": 1827,
      "description": "Identify epithelial tissue...",
      "options": ["Squamous", "Cuboidal", "Columnar"],
      "correct_option": 2
    }
  ]
}
Historical Quiz Data

Metrics tracked: score, accuracy, response_map (question-level responses).

Usage <a name="usage"></a>
Generate Recommendations:


# Sample output
{
  "weak_topics": ["Plant Physiology", "Organic Chemistry"],
  "recommended_study_time": "6 hours/day",
  "focus_areas": {
    "Hard": "Solve 5 thermodynamics problems daily"
  }
}
Predict Rank:


# Input: Student's quiz performance
predicted_rank = model.predict([[75, 0.8, 0.9]])
print(f"Predicted NEET Rank: {predicted_rank[0]}")
Results 
Visualizations
Topic Distribution
Figure 1: 70% questions from Biology, 20% from Chemistry

Recommendations

{
  "Difficulty": "Medium",
  "Practice_Strategy": "Revise NCERT diagrams for 2 hours",
  "Question_Count": 43
}

Model Performance

Model	MSE	R² Score
Linear Regression	80,439	0.68
Random Forest	49,260,360	0.76
Future Enhancements 
Student Personas

Labels like "Time-Crunched Learner" or "Concept Master".

Real-Time Integration

Connect to NEET Testline app via APIs.

Advanced Analytics

Natural Language Processing (NLP) for question similarity.

Your Name : Faisal hayat
LinkedIn : https://www.linkedin.com/in/faisal-hayat-734b4a2b0

Contact :
For questions or feedback:
Email : faishal8960@gmail.com 
