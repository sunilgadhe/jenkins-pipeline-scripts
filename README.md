**Jenkins Pipeline Script for AWS Glacier File Retrieval and Processing
**This Jenkins pipeline script automates the process of retrieving files from AWS Glacier, filtering them based on specific criteria, and copying them to a temporary S3 bucket for further processing.

Key Features
Workspace Cleanup:

Ensures a clean working environment by removing temporary directories.
Date Computation:

Computes the range of months between the provided start and end dates to process files within the specified time frame.
File Retrieval from AWS Glacier:

Retrieves file metadata from an S3 bucket.
Filters files based on source names and crawl types.
Restores files from AWS Glacier for a specified duration.
File Copying:

Copies the restored files to a temporary S3 bucket for further usage.
Error Handling:

Ensures graceful error handling with appropriate status updates.
Notification:

Sends email notifications to specified recipients with build details and logs.
Prerequisites
Jenkins Plugins:

AWS Credentials
Email Extension Plugin
AWS Configuration:

AWS IAM credentials with sufficient permissions to interact with S3 and Glacier.
Environment Variables:

bucket_name: Name of the S3 bucket.
jira_ticket: Identifier for tracking the task.
source_name: List of source names.
crawl_type: List of crawl types.
start_date and end_date: Date range for processing.
Script Workflow
Setup:

Cleans up the Jenkins workspace and prepares the environment.
Date Calculation:

Computes a list of months between start_date and end_date.
File Listing:

Retrieves file metadata from the specified S3 bucket.
Filters files based on the source and type criteria.
Glacier Restoration:

Initiates restoration of files from Glacier for a specified duration.
File Transfer:

Copies restored files to a temporary S3 bucket.
Notification:

Sends email notifications with the build status and log details.
Usage
Configure the script parameters in your Jenkins job:

start_date
end_date
bucket_name
source_name
crawl_type
Trigger the Jenkins pipeline.

Monitor the console output for progress and check your email for the final status.

Error Handling
The script ensures robust error handling:

It catches exceptions during the pipeline stages and marks the build as FAILURE.
Logs and emails provide detailed insights into the failure for debugging.
Email Notifications
An email is sent upon completion of the pipeline, providing:

Build status (SUCCESS or FAILURE).
Link to the console output for detailed logs.
