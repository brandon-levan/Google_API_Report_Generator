# Google API Report Generator

This solution was designed under the assumption that your organization can generate a daily Google Sheet that contains data for that day or cumulative up to that day. These Google Sheets may have data all on one sheet or across multiple sheets. These Google Sheets can contain tables or charts. The Google Sheets will be stored in a Google Drive Folder and all Google Sheets will be written to that same folder. Additionally, this solution is works under the assumption that there is a template that your organization likes to use for presenting the data. There will be one Google Slides template, and this presentation will be copied each time a new presentation is needed and data from that day’s Google Sheet will be written to the copy of the template. All of the presentations will be saved in a Google Drive folder accessible to anyone who needs the presentation. 

Script Logic - When the Python script is run, it will follow these rules - 
  - Check if there is a Google Sheet with data for the current day in the folder
      - No - If no Google Sheet for current day, do nothing
      - Yes - If there Google Sheet for current day
          - Check if there is a Google Slide presentation already available for the current day in the folder
              - Yes - Delete the presentation and create a new one using the data in Google Sheet for the current day (There may have been a change to the data in the Google Sheet so we need make sure we delete the old presentation and replace it with a new one with accurate data).
              - No - Create a new Google Slide presentation using the data in Google Sheet for the current day
