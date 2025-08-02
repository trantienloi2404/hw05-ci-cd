# API Testing Assignment - Student ID: 22127240   

## Project Overview
This repository contains the complete API testing assignment for CS423 - Software Testing course. The project focuses on testing the Favorite APIs of The Toolshop application using data-driven testing approach.

## Project Structure
```
├── 22127240_APITesting.md          # Main report (Markdown format)
├── 22127240_TestCases.xlsx         # Test cases in Excel format
├── 22127240_BugReport.xlsx         # Bug report in Excel format
├── data/                           # Test data files
│   ├── post_favorite_test_data.csv
│   ├── get_favorite_test_data.csv
│   └── delete_favorite_test_data.csv
├── Favorite API Tests - Data Driven.postman_collection.json
├── Favorite API Environment.postman_environment.json
└── .github/workflows/api-tests.yml # CI/CD workflow
```

## APIs Tested
1. **POST /favorites** - Add product to favorites
2. **GET /favorites** - Get user's favorites
3. **DELETE /favorites/{id}** - Remove favorite

## Setup Instructions
1. Clone the repository
2. Install Node.js dependencies: `npm install`
3. Start the application: `npm start`
4. Import Postman collection and environment files
5. Run tests using Newman or Postman

## CI/CD Integration
The project includes GitHub Actions workflow for automated testing:
- Runs on push to main branch
- Uses Newman to execute Postman collections
- Generates test reports
- Publishes results to GitHub

## Video Demonstrations
- API Testing Process: [YouTube Link]
- CI/CD Integration: [YouTube Link]

## AI Tools Usage
This project demonstrates effective use of AI tools for:
- Test case design
- Bug analysis
- Documentation
- CI/CD configuration

## Assessment
Self-Assessment Score: 10.0/10.0
- API1 (POST): 3.0/3.0
- API2 (GET): 3.0/3.0  
- API3 (DELETE): 3.0/3.0
- AI Tools Usage: 1.0/1.0 