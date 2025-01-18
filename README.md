README

This repository contains three main projects:

Frontend Development: A responsive webpage.

Django Application: A chat application with WebSocket support.

AWS Lambda Functions: Serverless functions for adding numbers and uploading documents to an S3 bucket.

Frontend Development

Prerequisites

Modern web browser (Chrome, Firefox, Edge, etc.)

Code editor (e.g., VS Code) for modifications

Steps to Run

Navigate to the frontend folder.

Open index.html in a web browser.

The webpage should display the fixed navbar, collapsible left menu, main content area, right-side panel, and footer.

Notes

Modify the styles.css file to customize the appearance.

JavaScript functionality is provided in script.js.

Django Application

Prerequisites

Python 3.9 or above

Virtual environment module

Django and Django Channels installed

Installation Steps

Navigate to the Django folder:

cd Django

Create and activate a virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

Install dependencies:

pip install -r requirements.txt

Apply migrations:

python manage.py migrate

Run the server:

python manage.py runserver

Open a browser and navigate to http://127.0.0.1:8000/.

Notes

Modify settings.py for database or other configurations.

WebSocket functionality is implemented in consumers.py.

AWS Lambda Functions

Prerequisites

AWS CLI configured with appropriate permissions

Python installed locally

Folder Structure

AWS/
  lambda_functions/
    add_numbers/
      handler.py
    upload_to_s3/
      handler.py
  deployment/
    add_numbers.zip
    upload_to_s3.zip

Steps to Deploy

Navigate to the respective Lambda function folder:

cd AWS/lambda_functions/add_numbers

Compress the function code:

zip -r ../../deployment/add_numbers.zip handler.py

Repeat for upload_to_s3:

zip -r ../../deployment/upload_to_s3.zip handler.py

Deploy using AWS Management Console or CLI:

aws lambda create-function \
  --function-name addNumbers \
  --runtime python3.9 \
  --role <execution-role-arn> \
  --handler handler.lambda_handler \
  --zip-file fileb://../../deployment/add_numbers.zip

Repeat for upload_to_s3.zip.

Notes

Replace <execution-role-arn> with your Lambda execution role ARN.

Ensure your S3 bucket exists before using the upload_to_s3 function.

General Notes

Use requirements.txt files to track dependencies.

Ensure proper environment setup and configurations for smooth deployment and testing.

