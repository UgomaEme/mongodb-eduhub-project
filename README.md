# mongodb-eduhub-project
Eduhub Project (Second Semester)

This project showcases a MongoDB-based backend system for an e-learning platform called EduHub, implemented using PyMongo in a Jupyter Notebook and exported as a Python script.

PROJECT SETUP INSTRUCTIONS
1. Clone the repository (if hosted on GitHub):
git clone https://github.com/emeugoma/eduhub-mongodb-project.git
cd eduhub-mongodb-project
2. Create a virtual environment (optional but recommended):
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
3. Install required packages:
pip install pymongo pandas jupyter.
4. Start your MongoDB server locally (ensure MongoDB is installed)
5. Open the Jupyter Notebook (optional):
jupyter notebook eduhub_mongodb_project.ipynb
6. Or run the Python script directly:
python eduhub_queries.py

🧱 DATABASE SHCEMA DOCUMENTAION
 
Users Collection

{

  "user_id": "U001",
  "first_name": "Amy",
  "last_name": "Smith",
  "email": "amy75@example.net",
  "role": "student",         // student or instructor
  "date_joined": ISODate(),
  "is_active": true,
  "profile": {
    "bio": "Learning enthusiast",
    "avatar": "https://api.dicebear.com/6.x/thumbs/svg?seed=Amy",
    "skills": ["Python", "MongoDB"]
  }
  
}

Courses Collection

{
  "course_id": "C001",
  "title": "Intro to MongoDB",
  "description": "...",
  "price": 49.99,
  "tags": ["MongoDB", "Database"],
  "is_published": true
}

Submissions Collection
{
  "submission_id": "S001",
  "user_id": "U001",
  "course_id": "C001",
  "grade": 89.5
}

 🔍 QUERY EXPLANATIONS
- User Profile Update: Update nested fields using $set.
- Email Lookup: Indexing the email field speeds up lookup performance.
- Course Publishing: Updates the is_published field.
- Recommendations: Uses $match, $setIntersection, $addFields, and $sort in an aggregation pipeline to recommend courses.
- Average Grade: Groups submissions by user_id to calculate average grades.
- Recent Users: Filters users by date_joined within the last 180 days.

🚀 PERFORMANCE ANALYSIS RESULTS

Indexes Used:
- email field in users
- user_id in submissions
Tags in courses for recommendation matching:
- Aggregation Optimization:
- Using $setIntersection avoids expensive application-side filtering.
- $limit and $sort efficiently prioritize top recommendations.

⚠️ CHALLENGES FACED AND SOLUTIONS
1. Validation Errors on Collection Creation

Problem: Repeated errors when creating collections with $jsonSchema. Solution: Ensure the collection is dropped before re-creating it or wrap creation in a try/except block.

2. Data Not Found in Queries

Problem: Many lookups returned "user not found". Solution: Manually verify inserted data and correct field names. Used .find_one() checks with error messages.

3. Date Filtering Issues

Problem: date_joined filter returned no users. Solution: Ensured inserted datetime objects were in the correct format and timezone.

4. Notebooks Not Saving

Problem: Unsaved notebooks failed to create proper scripts. Solution: Saved the notebook manually before exporting to .py.

📁 FILES

- eduhub_mongodb_project.ipynb – Development notebook

- eduhub_queries.py – Clean backup script of all queries

- README.md – Project documentation (this file)

📌 AUTHOR

EME UGOMA

AltSchool Data Engineering – MongoDB Project (2024)













 
