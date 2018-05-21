# Nametags

## Overview

We print three different kinds of nametags: delegate nametags, which are double-sided and have each delegate's information on them, faculty nametags, which are single-sided and have just the school name, and staff nametags, which are also single-sided and have the staff position. 

All of the nametags are templated in InDesign, generated with Data Merge, and then exported to PDF and printed. Nametag design is relatively simple \(as they don't change year by year and most of the heavy lifting comes from computing\), but it's important to look out for edge cases, such as spelling errors, non-Unicode characters, and cutoff text.

## Examples

![A Staff Nametag](../.gitbook/assets/screen-shot-2018-05-21-at-3.18.02-pm.png)

![A Delegate Nametag](../.gitbook/assets/screen-shot-2018-05-21-at-3.20.13-pm.png)

## Data Collection

Before any designing can be done, all the data for the nametags needs to be centralized into one file. 

## Data Merge

Data Merge is a powerful tool in Adobe InDesign that allows you to create a template file and export many copies of that file, with data populated from an input source. We use Data Merge to generate our nametags from information in an excel spreadsheet.

### File Type

To use Data Merge, the input file needs to have the right file type. We recommend using either Comma Separated Values `.csv` file \(which can be exported from Excel or Google Sheets\), or a UTF-16 Unicode Text `.txt` file \(which can be exported from Excel\). Usually, a CSV is fine, but if the nametag values contain special characters \(e.g. é, ç, ü\) then you must use UTF-16 Unicode encoding to maintain the special characters.

### Format

Data Merge interprets different types of values \(e.g. School, Name, Position\) by a header row, where each column is a specific type of data. 

![In this example, there are two data types: Position, and Name](../.gitbook/assets/screen-shot-2018-05-21-at-2.50.25-pm.png)

Then, select the Data Merge option in InDesign, and use "Select Data Source" to select your data. The resulting menu should show each of the data types you had.

![In this example, InDesign recognizes the two data types from the previous example.](../.gitbook/assets/screen-shot-2018-05-21-at-2.52.32-pm.png)

### Layout

To use these data types, simply create text boxes and type in `<<Type Name>>` . You can also double-click the data type in the Data Merge menu to automatically put it into the document. This text is manipulatable like any other text.

![The WAC 2018 staff nametag skeleton template](../.gitbook/assets/screen-shot-2018-05-21-at-2.55.39-pm.png)

While designing layouts using Data Merge, keep in mind the length of the possible data values: for long data such as delegate or school names, sufficient space is needed to allow the text to wrap into multiple lines. If not, some names will be cut off, which isn't fun for anybody!

If space allows, we suggest that you turn off hyphenation for text blocks, as they can be visually jarring and confusing. You can do this in the paragraph menu.

![](../.gitbook/assets/screen-shot-2018-05-21-at-3.01.04-pm.png)

### Generating and Exporting

You can preview how a generated document by selecting "Preview", or use "Create Merged Document" to create an InDesign document with a spread for each set \(row\) of your data.

![A Preview of a Staff Nametag](../.gitbook/assets/screen-shot-2018-05-21-at-3.07.08-pm.png)

To create a final document to print, click "Export to PDF". The wide majority of settings are unimportant, though there are a few tidbits that are:

* Enable "Generate Overset Text Report" - this allows you to see if there's any overset text
* Use Single Record per Document Page, as our document is set up for one nametag per spread.
* Merge All Records - there's no reason not to!
* The "High Quality Print" Preset is usually sufficient, though you can fiddle around with the settings if needed.

After exporting, you should have a PDF that you can send to print. We suggest that you take a cursory look through some of the nametags, just to be sure that there aren't any problems.

