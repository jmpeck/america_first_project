# america_first_project

# creator: John Peck

Overview: This project tracks the appearance of "America first" in newspapers between 1900 and 1922. My goal was to investigate whether the phrase occurred more frequently around events like the outbreak of World War I and the formation of the League of Nations. 

My data: The Library of Congress and the National Endowment for the Humanities offer access to around 100,000 digitized historical newspaper pages through a website called "Chronicling America." Information can be found here: https://chroniclingamerica.loc.gov/about/.

Methods: Using the collection's API, I have written code that uses the Library of Congress's search function to find instances of the phrase "America first" and pulls the results in JSON form. For simplicity's sake at this stage of the process, I stripped out everything but the newspaper page's date. I was only interested in how often "America first" occurs in the database per year.

Because I was unsure about the representation of each year in the library's digital collection, I also ran an empty search through the API to see the relative frequency of each year in the collection of pages. My fear was that I might see a spike in "America first" mentions in 1916 simply because the Library of Congress had more pages from 1916, for example.

In the end, I had two sets: a set of "America first" mentions per year and a set of non-searched pages per year. Initially, I created these sets by simply asking the API to return the first 1000 entries in each case. After checking the representation of each year in these initial runs though, I decided in each case to ask the API for a randomly selected 1000 entries (actually 50 randomly selected pages of 20 results). The relative yearly representation of these sets appeared much less skewed.

I calculated the weighted appearance frequency of the phrase "America First" by dividing the instances for a certain year in my "America first" set by the instances for that year in my empty-search set.  For example, if 1916 occurs 99 times in the first set and 90 times in the second set, the weighted appearance frequency would be 1.1.

Graph: Using Bokeh, I created a line graph showing the weighted appearance frequency (y-axis) over the years 1900-1922 (x-axis)

Conclusions: There is a clear rise in the frequency of the phrase "America first" after the outbreak of WWI in 1914. This rise continues through 1917 when America entered the war. There is also a slight rise in the phrase's frequency in the lead up to the founding of the League of Nations.

Unexpectedly 1906 often shows a spike when running the data. This spike is presumably related to the "See America First" movement, a tourism campaign that began in Salt Lake City that year. In the future, I need to refine the program to remove such instances, especially because this campaign continued into the 1910's.

Further refinement will also lead to storing the month as part of the date information I'm collecting. This will allow me to more clearly find connections between world events and the occurrence of the phrase "America first."

Ideally my technical skills will evolve to the point that I can sample the library's collection of newspapers with better accuracy and comprehension

To run: Run America_First_Frequency_Graph_delivered.ipynb with JupyterNotebooks. You will need python and JupyterNotebooks. The script also uses the following import statements:

  import requests
  
  import from collections import Counter
  
  import random
  
  import sqlite
  
  from bokeh.io import show, output_notebook
  
  from bokeh.plotting import figure, output_file, show
  
  from bokeh.models import HoverTool, FuncTickFormatter, FixedTicker, ColumnDataSource
