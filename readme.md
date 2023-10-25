# Jira Backup Script Readme

This README explains the purpose and functionality of the provided bash script for creating backups of a Jira instance using the Jira REST API. The script is designed to be customized for your specific Jira instance and backup needs.

## Purpose

The primary purpose of this script is to automate the process of creating backups of a Jira instance. It uses the Jira REST API to trigger the backup process, monitor the progress of the backup, and download the backup file once it's ready.

## Configuration

Before running the script, ensure that you configure the following variables in the "CONFIGURATION SECTION" of the script:

1. `EMAIL`: Replace with the email associated with your Jira account.
2. `API_TOKEN`: Replace with your Jira API token.
3. `INSTANCE`: Set to the name of your Jira instance.
4. `DOWNLOAD_FOLDER`: Specify the local directory where you want to save the backup files.
5. `INCLUDE_ATTACHMENTS`: Set to `true` if you want to include attachments in the backup, or `false` if not.
6. `EXPORT_TO_CLOUD`: Set to `true` if you want to create a backup for Jira Cloud, or `false` if you are using Jira Server.
7. `PROGRESS_CHECKS`: Number of times the script will check the backup progress.
8. `SLEEP_SECONDS`: Number of seconds to wait between each progress check.
9. `TIMEZONE`: Set to your Jira instance's timezone, e.g., "Asia/Jakarta."

Make sure to fill in these configuration variables with the correct values relevant to your Jira instance.

## Script Execution

When you run the script, it will perform the following steps:

1. Get the current date and time based on the specified timezone.
2. Send a request to the Jira REST API to initiate a backup.
3. Check the response for errors, and if there are any errors, the script will exit.
4. If the backup is started successfully, the script extracts the `taskId` from the response.
5. It then repeatedly checks the progress of the backup using the `taskId`, waiting between checks based on the `SLEEP_SECONDS` variable.
6. Once the backup is completed and a backup file is available, it will be downloaded to the specified `DOWNLOAD_FOLDER`.
7. The script ends.

## Error Handling

The script monitors the progress of the backup and checks for errors at each step. If an error is encountered, it will exit the script. It also has a mechanism to handle backups that take longer to complete, but if a backup is not ready after the configured number of progress checks, the script will exit.

## Important Note

Before using the script, ensure that your Jira instance is accessible via the specified URL and that the provided email and API token have the necessary permissions to perform backups.

**Note:** This script is a basic example and may need further customization based on the specific requirements and constraints of your Jira instance.