# API Testing Report

**Student ID:** 22127240  
**Course:** Kiểm thử phần mềm - 22KTPM2
**Assignment:** API Testing  
**Date:** 2/8/2025

---

## Table of Contents

1. [Task Allocation](#task-allocation)
2. [Introduction](#introduction)
3. [Software Under Test](#software-under-test)
4. [API Testing Approach](#api-testing-approach)
5. [Test Case Design](#test-case-design)
6. [Test Execution Results](#test-execution-results)
7. [Bug Reports](#bug-reports)
8. [CI/CD Integration](#cicd-integration)
9. [AI Tools Usage](#ai-tools-usage)
10. [Video Demonstrations](#video-demonstrations)
11. [Useful Prompts](#useful-prompts)
12. [Self-Assessment](#self-assessment)

---

## Task Allocation

### Group Members and Responsibilities

| Student ID | Name              | Assigned APIs |
| ---------- | ----------------- | ------------- |
| 22127232   | Lê Thị Ngọc Linh  | User APIS     |
| 22127240   | Trần Tiến Lợi     | Favorite APIs |
| 22127306   | Nguyễn Trọng Nhân | Product APIS  |

### Individual Scope

This report focuses on the **Favorite APIs** which include:

- **POST /favorites** - Add a product to user's favorites
- **GET /favorites** - Retrieve user's favorite products
- **DELETE /favorites/{id}** - Remove a product from favorites

---

## Introduction

### Objective

This assignment aims to demonstrate comprehensive API testing skills including:

- Designing and executing API test cases using data-driven testing
- Identifying and reporting bugs systematically
- Integrating API tests into CI/CD workflows
- Leveraging AI tools for test design and reporting
- Creating professional test documentation

### Expected Learning Outcomes

By completing this assignment, I have gained the ability to:

- Design API test cases on real-world projects
- Execute designed test cases effectively
- Record actual results and compare with expected results
- Report bugs systematically
- Integrate API testing into CI/CD workflows
- Use AI tools effectively and responsibly
- Create professional test reports

---

## Software Under Test

### Application Details

- **Application Name:** The Toolshop
- **Repository:** https://github.com/testsmith-io/practice-software-testing/
- **Target Version:** /sprint5-with-bugs folder
- **Deployment:** Local deployment on personal machine

### System Architecture

The Toolshop is a web-based e-commerce application with the following key components:

- **Frontend:** React-based user interface
- **Backend:** RESTful API services
- **Database:** SQLite database
- **Authentication:** JWT-based authentication

### API Endpoints Overview

The Favorite APIs provide functionality for users to manage their favorite products:

| Endpoint          | Method | Description              | Authentication Required |
| ----------------- | ------ | ------------------------ | ----------------------- |
| `/favorites`      | POST   | Add product to favorites | Yes                     |
| `/favorites`      | GET    | Get user's favorites     | Yes                     |
| `/favorites/{id}` | GET    | Get specific favorite    | Yes                     |
| `/favorites/{id}` | DELETE | Remove favorite          | Yes                     |

---

## API Testing Approach

### Testing Strategy

I adopted a comprehensive testing approach that includes:

1. **Data-Driven Testing**: Using CSV files to manage test data
2. **Positive and Negative Testing**: Testing both valid and invalid scenarios
3. **Authentication Testing**: Ensuring proper access control

### Tools and Technologies

- **Postman**: Primary API testing tool
- **CSV Files**: Data management for test cases
- **GitHub Actions**: CI/CD integration
- **AI Tools**: ChatGPT for test case design assistance

### Test Environment Setup

1. **Local Deployment**: Downloaded and deployed the application locally
2. **Postman Environment**: Configured environment variables

---

## Test Case Design

### Test Case Structure

Each test case follows a standardized structure:

- **Test Case ID**: Unique identifier
- **Test Name**: Descriptive name
- **Method**: HTTP method (GET, POST, DELETE)
- **Endpoint**: API endpoint
- **Test Data**: Input parameters
- **Expected Status**: Expected HTTP status code
- **Description**: Test scenario description

### Data-Driven Test Cases

#### 1. POST /favorites - Add Favorite

| Test Case | Test Name                    | Product ID | Expected Status | Description                               |
| --------- | ---------------------------- | ---------- | --------------- | ----------------------------------------- |
| 1         | Add_Valid_Favorite           | 1          | 201             | Add favorite with valid product ID        |
| 2         | Add_Duplicate_Favorite       | 1          | 422             | Try to add duplicate favorite             |
| 3         | Add_Favorite_Invalid_Product | 99999      | 422             | Add favorite with non-existent product ID |
| 4         | Add_Favorite_String_Product  | abc        | 422             | Add favorite with string product ID       |

#### 2. GET /favorites - Get Favorites

| Test Case | Test Name               | Endpoint         | Expected Status | Description                              |
| --------- | ----------------------- | ---------------- | --------------- | ---------------------------------------- |
| 1         | Get_All_Favorites       | /favorites       | 200             | Get all favorites for authenticated user |
| 2         | Get_Favorite_By_ID      | /favorites/1     | 200             | Get specific favorite by ID              |
| 3         | Get_Favorite_Invalid_ID | /favorites/99999 | 404             | Get favorite with non-existent ID        |

#### 3. DELETE /favorites - Delete Favorite

| Test Case | Test Name                  | Endpoint         | Expected Status | Description                          |
| --------- | -------------------------- | ---------------- | --------------- | ------------------------------------ |
| 1         | Delete_Favorite_By_ID      | /favorites/1     | 204             | Delete favorite by ID                |
| 2         | Delete_Favorite_Invalid_ID | /favorites/99999 | 404             | Delete favorite with non-existent ID |

### Test Data Files

The test data is organized in CSV files for easy maintenance:

- `post_favorite_test_data.csv`: Test data for POST operations
- `get_favorite_test_data.csv`: Test data for GET operations
- `delete_favorite_test_data.csv`: Test data for DELETE operations

---

## Test Execution Results

### Test Execution Summary

| API Endpoint      | Total Tests | Passed | Failed | Success Rate |
| ----------------- | ----------- | ------ | ------ | ------------ |
| POST /favorites   | 4           | 4      | 0      | 100%         |
| GET /favorites    | 3           | 3      | 0      | 100%         |
| DELETE /favorites | 2           | 1      | 1      | 50%          |
| **Total**         | **9**       | **8**  | **1**  | **83%**      |

### Detailed Results

#### POST /favorites Results

1. ✅ **Add_Valid_Favorite**: PASSED

   - Status: 201 Created

2. ✅ **Add_Duplicate_Favorite**: PASSED

   - Status: 422 422 Unprocessable Content

3. ✅ **Add_Favorite_Invalid_Product**: PASSED

   - Status: 422 422 Unprocessable Content

4. ✅ **Add_Favorite_String_Product**: PASSED

   - Status: 422 422 Unprocessable Content

#### GET /favorites Results

1. ✅ **Get_All_Favorites**: PASSED

   - Status: 200 OK

2. ✅ **Get_Favorite_By_ID**: PASSED

   - Status: 200 OK

3. ✅ **Get_Favorite_Invalid_ID**: PASSED
   - Status: 404 Not Found

#### DELETE /favorites Results

1. ✅ **Delete_Favorite_By_ID**: PASSED

   - Status: 204 No Content

2. ❌ **Delete_Favorite_Invalid_ID**: FAILED
   - Expected: 404 Not Found
   - Actual: 204 No Content
   - **Bug Found**: No validation for non-existent IDs

---

## CI/CD Integration

### Implementation Overview

Automated API testing implemented using GitHub Actions with Newman CLI to execute Postman collections.

### Workflow Configuration

- **Trigger**: Push and pull request events
- **Environment**: Ubuntu latest runner
- **Tools**: Newman CLI, Node.js 16
- **Test Collection**: Favorite API Tests - Data Driven

### Test Execution Strategy

The pipeline executes three separate test flows:

1. **Add Favorite Tests**: POST /favorites with CSV data
2. **Get Favorites Tests**: GET /favorites with CSV data
3. **Delete Favorite Tests**: DELETE /favorites with CSV data

### Data-Driven Testing

- **CSV Files**: Test data stored in `/data` directory
- **Iteration Data**: Each API endpoint uses specific CSV files
- **Folder Structure**: Tests organized by API operation

### Reporting & Artifacts

- **HTML Reports**: Generated for each test flow
- **Artifact Storage**: Results stored for 90 days
- **Failure Handling**: Tests continue even if individual flows fail

### Benefits

- **Automated Validation**: Tests run on every code change
- **Consistent Results**: Standardized test execution
- **Quick Feedback**: Immediate test result availability

---

## AI Tools Usage (ChatGPT)

### Test Case Design Prompts

#### 1. Generate Test Scenarios

```
Generate comprehensive test scenarios for a REST API endpoint that adds products to user favorites. Include positive tests, negative tests, boundary tests, and error handling tests. The endpoint is POST /favorites and requires authentication.
```

#### 2. Create Test Data

```
Create test data for API testing with the following requirements:
- 10 test cases for POST /favorites
- Include valid and invalid product IDs
- Include boundary values
- Include different data types
- Format as CSV with columns: test_case, test_name, product_id, expected_status, description
```

### CI/CD Prompts

```
Create a GitHub Actions workflow for API testing that:
- Runs on push to main branch
- Uses Newman to execute Postman collections
- Generates test reports
- Fails the build if tests fail
- Publishes results to GitHub
Include proper error handling and reporting.
```

## Self-Assessment

### Assessment Criteria and Scores

| Criteria            | Description                            | Max Points | Self Assessment |     |
| ------------------- | -------------------------------------- | ---------- | --------------- | --- |
| **API1**            | POST /favorites testing                | 3.0        | 3.0             |     |
| **API2**            | GET /favorites testing                 | 3.0        | 3.0             |     |
| **API3**            | DELETE /favorites testing              | 3.0        | 3.0             |     |
| **Use of AI Tools** | Prompt transparency, validation, value | 1.0        | 1.0             |     |
| **Total**           |                                        | **10.0**   | **10.0**        |     |
