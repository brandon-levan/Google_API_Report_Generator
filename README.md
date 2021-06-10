# Google API Report Generator

Imagine a world in which you never have to copy and paste values, tables, and charts into a presentation again. Google Workspace Solutions takes this concept and turns it into reality. REST APIs make it easy to programmatically interact with your Google Workspace and automate tasks with simple code. By developing a Python script that integrates with Google Drive, Sheets, and Slides, I am able to automate the report creation process that is usually performed manually by data analysts or account managers. This post will walk you through how you can leverage Google Developer Tools to automate your reporting and save valuable time for your organization.

This solution was designed under the assumption that your organization can generate a daily Google Sheet that contains data for that day or cumulative up to that day. These Google Sheets may have data all on one sheet or across multiple sheets. These Google Sheets can contain tables or charts. The Google Sheets will be stored in a Google Drive Folder and all Google Sheets will be written to that same folder. Additionally, this solution is works under the assumption that there is a template that your organization likes to use for presenting the data. There will be one Google Slides template, and this presentation will be copied each time a new presentation is needed and data from that day’s Google Sheet will be written to the copy of the template. All of the presentations will be saved in a Google Drive folder accessible to anyone who needs the presentation. 

Script Logic - When the Python script is run, it will follow these rules - 
  - Check if there is a Google Sheet with data for the current day in the folder
      - No - If no Google Sheet for current day, do nothing
      - Yes - If there Google Sheet for current day then
          - Check if there is a Google Slide presentation already available for the current day in the folder
              - Yes - Delete the presentation and create a new one using the data in Google Sheet for the current day (There may have been a change to the data in the Google Sheet so we need make sure we delete the old presentation and replace it with a new one with accurate data).
              - No - Create a new Google Slide presentation using the data in Google Sheet for the current day
