# 📌 Internship Auto-Application System (via Telegram + n8n)

## 🔍 Overview
This n8n workflow automates the process of applying to internship/job opportunities by leveraging AI-powered text analysis and email generation. Triggered via Telegram bot, the workflow extracts insights from job descriptions, fetches the appropriate CV, crafts a professional email, and stores all the relevant information in a Google Sheet for tracking.

## 🔁 Workflow Steps & Functional Breakdown

### 1. Trigger (Telegram Bot)
- Triggered when a user sends a job or internship description via Telegram.
- Captures the text message content and initiates the workflow.

### 2. Preprocessing 
- Trims and sanitizes the raw Telegram message to isolate the job description.

### 3. AI Analysis of Job Description
- Extracts:
  - Job Category (Data Analyst, Data Science, AI Engineer ,...)
  - Recruiter Email Address
  - LinkedIn Post Link (if present)
  - Language of the Job Description

### 4. Postprocessing AI Output
- Parses and validates the JSON response from the AI with fallback values.

### 5. CV Retrieval Based on Job Category
- Searches for the relevant CV in Google Drive based on the identified job category.
- Downloads and extracts text from the CV PDF.

### 6. Email Generation using AI
- Uses GPT-4o Mini to generate a professional email in the detected language.
- Email includes: greeting, interest, CV highlights, contact information.

### 7. Sending the Application
- Downloads the final CV version.
- Sends the email (with CV) to a predefined email address.

### 8. Tracking and Logging
- Records the job application info into Google Sheets, including:
  - Job Category
  - Recruiter Email
  - Language
  - LinkedIn Source
  - Status
  - Timestamp

## 📌 Technologies & APIs Used

| Component       | Tool/Service         |
|----------------|----------------------|
| Trigger         | Telegram Bot         |
| AI Processing   | OpenRouter (GPT-4o)  |
| File Handling   | Google Drive         |
| Email Sending   | Gmail API            |
| Logging         | Google Sheets        |
| PDF Processing  | n8n File Extraction  |

## ✅ Use Case
An intelligent assistant that automates and streamlines job/internship applications for data roles, saving time while ensuring quality and personalization.

## Prerequisites
### Required Credentials

  * **Telegram Bot API:** For receiving job descriptions
  * **OpenRouter API:** For GPT-4o Mini access
  * **Google Drive :** For CV storage and retrieval
  * **Gmail :** For sending applications
  * **Google Sheets :** For tracking submissions

### Required Setup

1. Google Drive Structure:

  - Folder containing CVs named by job category
  - PDF files: Data Analyst.pdf, Data science.pdf,...


2. Google Sheets Structure:

  - Columns: Post, Email Recruiter, Status, Send Date, Offer Description, Language, Source


3. Telegram Bot:

  - Configured webhook for message reception
  - Bot token properly configured

4. Usage Instructions
   
  For End Users
  
  - Send Job Description: Forward or type job description in Telegram chat
  - Automatic Processing: Workflow analyzes posting and generates application
  - Email Sent: Application email sent automatically with appropriate CV
  - Tracking Updated: Application logged in Google Sheets
