---
title: "Dates as Data"
teaching: 10
exercises: 10
questions:
- "What are good approaches for handling dates in spreadsheets?"
objectives:
- "Recognise problematic or suspicious date formats."
- "Use formulas to separate dates into their component values (e.g. Month, Day, Year)."
keypoints:
- "Use extreme caution when working with date data."
- "Splitting dates into their component values can make them easier to handle."
---

## Date formats in spreadsheets

Dates in spreadsheets are often stored in a single column. While this seems like a logical way to record dates when you are entering them, or visually reviewing data, it's not actually the best practice for preparing data for analysis.

When working with data, your goal is to have as little ambiguity as possible. Ambiguity can creep into your data when working with dates when there are regional variations either in your observations and when you or your team might be working with different versions or suites of software products (e.g., Google Sheets, LibreOffice, Microsoft Excel, Numbers, Gnumeric).

To avoid ambiguity between regional differences in date formatting and compatibility across spreadsheet software programs, a good practice is to divide dates into components in different columns - DAY (DD), MONTH (MM), and YEAR (YYYY).  

When working with dates it's also important to remember that functions are guaranteed to be compatible only within the same family of software products. If you need to export your data and conserve the timestamps, you are better off handling dates using the ISO format we will cover in a bit.

One of the other reasons dates can be tricky is that most spreadsheet programs have “useful features” which can change the way dates are displayed - but not stored. The image below demonstrates some of the many date formatting options. 

![Many formats, many ambiguities](../fig/dates_1.jpg) <br>

[Download and make a copy of the file](https://docs.google.com/spreadsheets/d/1OvuGrL9_f7sq2wUZM5aXAvzN4L-SwNL6z_9gUfjXzRk/edit?usp=sharing) if you want to follow this portion along.

You may explore more options available on Google Sheets `(Format> Number> Custom date and time...)`:

![Many formats, many ambiguities-2](../fig/dates_2.jpg) <br>


## Dates stored as integers

The first thing you need to know is that as most spreadsheets programs, Google Sheets stores dates as numbers. Because DATE values are stored as integers, you can use them in arithmetic expressions. For example, you can subtract a DATE value from another DATE value.
This serial number represents the number of days from December 31, 1899. But how can you obtain that number for the 10/10/2022 date? We may use the `DATEVALUE` function to obtain that number by typing in and use the autocomplete feature: `=DATEVALUE(F2)`, and we will get 44844. As for any other function in spreadsheets, we can reuse that and apply to the cells bellow. 


> ## More on Google Sheets Dates
> 
> - Inputs to `DATE` must always be numbers - if a string or a reference to a cell containing a string is provided, an error will be returned.
> - DATE will silently recalculate numeric dates which fall outside of valid month or day ranges. For example, DATE(1969,13,1), which specifies the illegal month 13, will create a date of 1/1/1970. Similarly, DATE(1969,1,32), which specifies the non-existent 32nd day of January, will create a date of 2/1/1969.
{: .callout}

Using functions we can  add days, months or years to a given date.
Say you had a research plan where you needed to conduct interviews with a
set of informants every ninety days for a year.

In our example above, in a new cell you could type:

~~~
=B2+90
~~~
{: .code}

And it would return

~~~
8-Jan

The format will follow the cell of reference in the formula. Test it if you would like to see the results for other cells. 
~~~
{: .output}

## Regional date formatting

When you enter a date into a spreadsheet it looks like a date although the spreadsheet program may
display different text from what you input. It does this to be 'helpful' but it often is not. 

For example if you enter '7/12/88' into a
Excel spreadsheet it may display as '07/12/1988' (depending on your version of Excel). These
are different ways of formatting the same date.

Different countries also write dates differently. If you are in the UK or Brazil, for example, you will interpret
the date above as the 7th day of December, however a researcher from the US will interpret the same entry as the 12th day of July. For Google Sheets, you may adjust the time and locale settings accordingly. But imagine you are working on a project with multiple collaborators from different countries. You can always define rules for data entry, but an easier way to prevent any future issues with dates is to treat them not as a single data point, but as
three distinct pieces of data. Separating dates into their component parts
will avoid this confusion, while also giving the added benefit of allowing you to compare, for
example data collected in January of multiple years with data collected in February of multiple years.

> ## If you choose to store dates as a single string, use ISO 8601
> If you choose keeping all date elements in one cell, to avoid regional conflicts, we recommend you use the International Standard Organization (ISO) 8601 format for dates which represents date and time by starting with the year, followed by the month, the day, the hour, the minutes, seconds and milliseconds. For example, 2020-07-10 15:00:00.000, represents the 10th of July 2020 at 3 p.m. (in local time as there is no time zone offset specified. Such strings will be correctly sorted in ascending or descending order, and following this standard will ensure your dates will be correctly processed by the receiving software. Remember to note the use of the ISO standard in your data documentation.
{: .callout}


> ## Separating dates into components
>
> Download and open the [SAFI-dates.xlsx](https://docs.google.com/spreadsheets/d/1iKPWigjeKpHxC--wQlZuSVcb-5WIJenm/edit?usp=sharing&ouid=101311538260511928101&rtpof=true&sd=true) file. This file
> contains a subset of the data from the SAFI interviews, including the dates on which the
> interviews were conducted. Make a copy and rename it with your last name (e.g., SAFI-dates-Curty), to ensure we will all be working on our individual copies of the file. 
>
>
> Extract the components of the date to new columns. For this we
> can use the built in functions:
>
> `=MONTH()`    
> `=DAY()`  
> `=YEAR()`
>
> Apply each of these formulas to its entire column.
> Make sure the new column is formatted as a number and not as a date.
>
> We now have each component of our date isolated in its own column. This will allow us
> to group our data with respect to month, year, or day of month for our analyses and will
> also prevent problems when passing data between different versions of spreadsheet
> software (as for example when sharing data with collaborators in different countries).
>
> > ## Solution
> > ![dates exercise 1](../fig/solution_exercise_1_dates.png)
> >
> > Note that this solution shows the dates in `MM_DD_YEAR` format.
> {: .solution}
{: .challenge}


> ## Default year
>
> What happens if you type in another cell `11/17`? How should `Day`, `Month`, and `Year` columns
> should populate for this new data point. What year is shown in the `Year` column?
>
> > ## Solution
> > If no year is specified, the spreadsheet program will assume you mean the current year
> > and will insert that value. This may be incorrect if you are working with historical data so
> > be very cautious when working with data that does not have a year specified within its date
> > variable.
> {: .solution}
{: .challenge}

## Proceed with Extra Caution when Dealing with Historical Dates

In short, spreadsheet programs were not designed to operate historical dates well. Google Sheets can't handle well dates prior to 1900-01-01. And Excel can't handle well anything prior to 1900-03-01 because they have considered 1900 a leap year, when in reality it is not! 

If you’re mixing historic data
from before and after this date, it will translate only the post-1900 dates into its internal format, thus resulting in mixed data. If you’re working with historic data, be extremely careful with your dates!

For historical dates, it is best practice to follow the advice for separating dates into components above and use a numerical value that is positive or negative depending on the era. For dates that are before the Common Era (often abbreviated as B.C.E/BCE, or older nomenclature as B.C./BC), the years should be  represented as negative values, while dates after 0 (abbreviated CE/C.E. or AD/A.D.) should be represented as positive values. For example, the date of March 15, 44 BCE in `Day`, `Month`, and `Year` columns could look like: `15`,`3`,`-44`.


{% include links.md %}
