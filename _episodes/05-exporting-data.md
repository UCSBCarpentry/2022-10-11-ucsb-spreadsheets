---
title: "Exporting Data"
teaching: 10
exercises: 5
questions:
- "How can we export data from spreadsheets in a way that is useful for downstream applications?"
objectives:
- "Store spreadsheet data in universal file formats."
- "Export data from a spreadsheet to a CSV file."
keypoints:
- "Data stored in common spreadsheet formats will often not be read correctly into data analysis software, introducing errors into your data."
- "Exporting data from spreadsheets to formats like CSV or TSV puts it in a format that can be used consistently by most programs."
---

## A Note on Data Formats

Storing the data you're going to work with for your analyses file formats such as `*.xls` or `*.xlsx` - isn't a good idea. Why?

Even though `*.xls` or `*.xlsx` extensions are considered open standards (ECMA-376, ISO/IEC 29500), they are closely tied to the MS Office Excel application, and these files can contain lots of features that only interpreted by Excel.
  
As an example of inconsistencies in data storage, do you remember how we talked about how spreasheet programs stores dates earlier? It turns out that 
there are multiple defaults for different versions of the software, and you can switch between them all. So, say you’re
compiling Excel-stored data from multiple sources. There’s dates in each file- Excel interprets them as their own internally consistent
serial numbers. When you combine the data, the software take the serial number from the place you’re importing it from, and interpret it
using the rule set for the software you’re using to work on the spreadsheet. Essentially, you could be adding errors to your data, and it wouldn’t
necessarily be flagged by any data cleaning methods if your ranges overlap.

Storing data in a universal, open, and static format will help deal with this problem. Try tab-delimited (tab separated values
or TSV) or comma-delimited (comma separated values or CSV). CSV files are plain text files where the columns are separated by commas,
hence 'comma separated values' or CSV. The advantage of a CSV file over an Excel/SPSS/etc. file is that we can open and read a CSV file
using just about any software, including plain text editors like TextEdit or NotePad. 

Data in a CSV file can also be easily imported into other formats and
environments, such as SQLite and R. We're not tied to a certain version of a certain expensive program when we work with CSV files, so
it's a
good format to work with for maximum portability and endurance. Most spreadsheet programs can save to delimited text formats like CSV
easily, although they may give you a warning during the file export.

To export files as CSV in Google Sheets, choose `file`, then `download` and select the format.


## Working Off-line

There might be cases researchers will be on the field, working from remote locations, and won't have stable or any connectivity to work with Google Sheets. The good news is that you can turn-on the offline access option to create, view, and edit files. 

*Before you turn on offline access:*

- You must be connected to the internet.
- You must use the Google Chrome or Microsoft Edge browser.
- Don't use private browsing.
- Install and turn on [Google Docs Offline Chrome extension](https://chrome.google.com/webstore/detail/google-docs-offline/ghbmnnjooekpmoecnnnilnnbdlolhkhi).
- Make sure you have enough available space on your device to save your files.

*How to turn on offline access:*

Open Google Chrome or Microsoft Edge. If on Chrome, make sure you are signed into your account.
Go to [drive.google.com/drive/settings](drive.google.com/drive/settings) or click on the gear icon on Google Drive, then Settings.
Check the box next to "Create, open, and edit your recent Google Docs, Sheets, and Slides files on this device while offline."


> ## What to do when your data contain commas?
> 
> In some datasets, the data values themselves may include commas (,). In that
> case, you need to make sure that the commas are properly escaped when saving
> the file. Otherwise, the software which you use (including Excel) will most
> likely incorrectly display the data in columns. This is because the commas
> which are a part of the data values will be interpreted as delimiters.
>
> If you are working with data that contains commas, the fields should be
> enclosed with double quotes. The spreadsheet software should do the right
> thing ([LibreOffice](https://www.libreoffice.org/download/download/) provides
> comprehensive options to import and export CSV files). However, it is always a
> good idea to double check that the file you are exporting can be read in
> correctly. For more of a discussion on data formats and potential issues with
> commas within datasets see [the Ecology Spreadsheets lesson discussion
> page](http://www.datacarpentry.org/spreadsheet-ecology-lesson/discuss/).
{: .callout}

{% include links.md %}
