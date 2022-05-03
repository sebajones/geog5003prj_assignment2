# geog5003prj_assignment2
The Black Death

The software has been designed and built to interactively model the number of weekly deaths in the Black Death outbreak in 1665. The weekly number of deaths is not known but can be modelled using the understood relationship between deaths and the number of rats caught per week in a 100-metre x 100-metre square and the average population density in a 100-metre x 100-metre square. Data on the average number of rats caught per week and average population density is available are utilised in this project to model the average weekly deaths in 1665. The model is incorporated into a piece of software to visualise the data and enable user interactivity.

The data
The software takes in files containing the average number of rats caught per week (rats.txt) and the average population density (parishes.txt). The population density averaged areas represent parishes, and the rats-caught averaged areas represent the domains of rat catchers. Each pixel represents a 100-metre x 100-metre area and the complete datasets represent a map of the study area. Using the csv package, the data are read using loops from text files and appended to nested lists within lists. The software displays a visualisation of the data on the screen. The matplotlib package is used to create and display the visualisation of the two maps. An appropriate colourmap is selected for the maps.

Calculating average deaths
The model iterates through the two datasets' values and passes them through an equation to calculate the average number of deaths per 100-metre x 100-metre square. Loops are utilised to iterate through the values within the nested lists for both lists. The equation calculating the number of deaths using this understood relationship is:
d = (0.8 x r) x (1.3 x p)

In this equation, d is the average number of deaths per week, r is the average number of rats caught per week, and p is the average population density. r and p are not equally weighted in this equation, so their values are multiplied by the weighting factor.

The loop carries out the equation and appends the result (d) to nested lists in a new list (multiply nested list - stackoverflow.com and append to nested lists – stackoverflow.com). The nested lists ensure the data still accurately represents the same geographic regions. The results are written to a new text file (average_deaths.txt), with each line in the text file representing a line on the visualisation. The resulting dataset representing the calculated average number of deaths is then visualised as a map alongside the first two maps and displayed to the user.

Interactive sliders
Interactive elements are introduced into the software to allow modification by the user of the weighting factors in the average weekly deaths equation. Sliders are built using the IPython widgets library and allow the user to increase and decrease a value input. By defining the weighting factors as variables in the script and inputting the variables into a slider each, the weighting factor can be adjusted by the user. The weighting factor variables are passed through the widgets using .interactivity().

Issue: The properties of the sliders are defined in the script, however, not all of these have applied properly to the slider. The default value sets correctly, but the min and max values do not seem to, nor does the description apply.

Update function
An update function (update_plot) updates the deaths data each time the slider input value is modified. Within this function, it reruns the deaths data calculation with the newly defined weighting factors. Each time the function is run, the deaths data is cleared first, otherwise the modified values would be added to the existing values instead of replacing them. The function then writes the results of the user-modified equation to a new text file (average_deaths_user_modified.txt), which is then overwritten each time this input is modified. The update function writing new data to the text file appears to work as it should.

Issue: When the slider input values are modified and the calculated deaths values along with them, the update function should also update the visualisation on the screen, but this does not seem to work. I’ve attempted to troubleshoot the problem, and think I’ve narrowed it down to the incorrect use of matplotlib.show() in the function. I think that something like .draw should be used within the function and then .show used after/outside the function (when setting interactivity of the widgets) but I cannot seem to get it to work.
