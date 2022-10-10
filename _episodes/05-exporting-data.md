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

Storing the data you're going to work with for your analyses in the
default spreadsheet file format (`*.xls` or `*.xlsx`) - isn't a good idea. Why?

- Because it is a proprietary format, and it is possible that in
  the future, technology won’t exist (or will become sufficiently
  rare) to make it inconvenient, if not impossible, to open the file.

- Other spreadsheet software may not be able to open files
  saved in a proprietary format.

- Different versions of the same spreadsshet software may handle data
  differently, leading to inconsistencies.

- Finally, more journals and grant agencies are requiring you
  to deposit your data in a data repository, and most of them require more reusable and interoperable formats.
  
- The above points in proprietary software also apply to open data formats used by LibreOffice and Google Sheets native format (`*.Gsheet`). These formats are not static and do not get parsed the same way by different software packages.
  
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

To export it as a CSV, choose `file`, then `download` and select the format.


## Working Off-line

There might be cases researchers might be on the field and on remote locations and won't have stable or any connectivity to work with Google Sheets. The good news is that you can turn-on the offline access option to create, view, and edit files. 

*Before you turn on offline access:*

- You must be connected to the internet.
- You must use the Google Chrome or Microsoft Edge browser.
- Don't use private browsing.
- Install and turn on Google Docs Offline Chrome extension.
- Make sure you have enough available space on your device to save your files.


*How to turn on offline access:*

- Open Google Drive.
- At the top right, click Settings Settings and then Settings.
- Turn on Offline setting. 
- If you are using Microsoft Edge, you will be redirected to the Chrome Web Store to download the Google Docs Offline extension.
- To work offline, open Google Sheets. 

> ## Tips for working offline
> You can turn on offline access from Sheets settings. If you turn on offline access for Sheets, all then Docs, Slides will also be available offline.
> Alternatively, to turn on offline access, open any spreadsheet. At the top, next to the file title, click See document status Cloud done and then Turn on and then Turn on.
> If you want to use offline access for another Google Account, make sure you're signed in to the right Chrome or Edge profile. Learn how to switch Chrome profiles. 
{: .callout}


> ## A note on R and `xls`
> 
> There are R packages that can read `xls` files (as well as
> Google sheets .Gsheets). It is even possible to access different
> worksheets in the `xls` documents. However, because these 
> packages parse data tables from proprietary and non-static
> software, there is no guarantee that they will continue to 
> work on new versions. Exporting your data to CSV or TSV
> format is much safer and more reproducible.
{: .callout}


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
