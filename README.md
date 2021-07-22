# sameer1khan.github.io
A timeline of work and eduction history using TimelineJS. 

### Purpose
This was an experiment to see how timeline.js can be used with a json file.

### Procedure
This experiment involved the following steps: 
  - A [TimelineJS3 Template spreadsheet](https://docs.google.com/spreadsheets/d/1pHBvXN7nmGkiG8uQSUB82eNlnL8xHu6kydzH_-eguHQ/template/preview) with data populated manually on Google Sheet was donwloaded as a csv file. 
  - The csv file was converted to a json file using [NUKnightLab/TimelineJS3/contrib/csv_to_json.py](https://github.com/NUKnightLab/TimelineJS3/blob/master/contrib/csv_to_json.py), which is used in this repo as "work-edu-timeline.json".
  - Using the documentation for "[Integrate Timeline using Javascript](https://timeline.knightlab.com/docs/instantiate-a-timeline.html)" the index.html file was created.
  - This webiste was then served via https://sameer1khan.github.io/

### Results and Discussion
The output works almost as desired when comparing it to the timeline made by using the "Published Google Spreadsheet" available here - https://tinyurl.com/sameer1khan.

The main issue with the embeded json method are:
  - A blank `end-date` of an `event` is incorrectly rendered as "January 1, 0" instead of not being rendered as the desired display result. 
  - `era` were not written out to json from the csv file using "csv_to_json.py". So they werne't rendered. 

Possible solution can be to produce the json file with `end-date` value as `None` or `Null` where it should be blank. This way timline.js can perhaps better recognize the field and render it correctly. 

Don't know why rows with `era` weren't written out to json. 

However the most important issue here is that the json file produced using this procedure is "static". It cannot incorporate the useful features of cell formulas of Google Sheet like `=Year(NOW())` for the year column of a sart or end date for a dymanicaly updated result.

### Conclusion
An improved and automated procedure of creating json files from the Template Google Sheet can help when serving the website content from a "Private" github repository. A way to automate the json file creation can be to use Google Apps Script or Sheets API to "export" the template sheet as a json file. And then just before serving the json file using "index.html", few convenience functions can insert current data-time into the the needed fields. 

It seems that if publishing the template google sheet to web is not a privacy issue, then using the spreadsheet method will be much faster and more stable for obtaining desired results with TimelineJS3.
