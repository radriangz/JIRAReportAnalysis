﻿# JIRAReportAnalysis

Brief description:
There was a need to spend less time when searching and retrieving data from some JIRA report excel files, thus, the idea for this program was conceived. The program is very simple, we just need data from certain columns, so, the program searches the header for the right word combinations, and then uses the indexes found (which are the column indexes) to retrieve the rest of the data in those indexes, as it finds the data it creates objects to store it, or it adds the new data to existing objects, the program stores these objects in a hashMap. Once it's done, the results are shown in a message window.

The data we need are the name of the employees, the original estimated time and the remaining estimated time.
The columns in which this data is have a header, the titles in the header we look for are:
  - "Responsable" for the employee name.
  - "Estimación original" for the original estimated time.
  - "Estimación Restante" for the remaining estimated time.
  
How this program works.
  When the program stars, it request the file to open through a fileChooser window, obtains the fileRoute and creates a JIRAReportAnalysis object, introducing the fileRoute as a parameter, the executeAnalysis() method is called, this method uses the fileRoute to obtain the sheet containing the table we need, assigns is to the class field 'sheet' and proceeds to call the method iterateSheetRows(), which assigns the sheet's iterator method to a rowIterator, then compares the next row to the constant value of the header (the header is the first row, so the value is the index 0 (this is the same for all the reports we use), the program iterates through the header row and obtains the indexes of the cells containing the text specified a while ago, assigns those indexes to class fields byt using the method findColumnIndexes(), and then proceeds to iterate through therest of the table rows using the method processResponsibleDataFromRow. In this method the data from the cells at the column index is obtained and assigned to local variables, one string and two double values, the string is used as a key for the hashMap, the method looks for that key in the hashMap, if it already exist, the object stored in that bucket is called and we use its methods to add the new values to the already stored values, if there is no key containing the string in the local variable, a new object is created with the string and double values and stored in the hashMap with the string as its key, this is done until there are no more rows left, at this point, the results are shown in a mesage window for the user to read them.

This project can be used executing the jar file in build folder.