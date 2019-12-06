# LCFC python3 application for UNIX (Leicester City Football Club)
Attempting to write a basic python3 program that will quickly tell users statistics, fixtures, scores & other information on Leicester City without having to manually search the internet. This is the second program i've ever created so there may be various inefficiencies and i am always welcome to advice if anyone ever finds this or wants to contribute.

Linux edition has just been created and I am still working through the conversion process, more files & information will be added very shortly to assist in functionality

Below is a brief outline of what each script attempts to accomplish:

# run.py
The main script used to start the application. This script acts as a central point for initial user queries concerning what data they would like to view. The file performs initial checks on its directory to confirm the presence of data files, if these are not there, it will download and save the latest files hosted in github.

Users can run an update tool which reads the version number from each data file for both internal scripts & externally hosted files. If the internal version number is lower, the program will query the user to update or continue using old files. 

The update mechanism renames it's current related scripts (.old) then uses headless Firefox & geckodriver to go to the embedded update link, copy the page source, parse with BeautifulSoup and finally copying this into a new file.

The user is presented with the main query listing functions & required input. Data is held on external script files (current_fixture_list.py, current_player_stats.py, current_results.py)

There is also a command function added to help with testing the program.

# run_update.py
The script automatically reads the version number for run.py or obtaining a read_file if one cannot be found, the version number is then compared to the latest script hosted on github. The update for run.py itself is then performed if a higher version number is found online, the process is performed using a similar syntax as the update function on run.py.

# run_restart.py
Called upon by run.py and calling run.py itself, this file acts as a restart function accessible via the "commands" section. This is sometimes needed to access updated files, might need to make the program perform this automatically after the update has been performed, I need to test more on this.

Not working as intended, see issues (#18)

# /version/read_version_xyz.py
All version files have an almost identical syntax with all outputting the current version number of its associated file. This is performed via reading the top line of the corresponding data file & converting the output to float for comparison.

These files should remain static, unless the version number syntax has to change.

# /data/current_fixture_list.py
User is presented with a query asking to see the next fixture, or a list of all. More details are available if viewed one by one. If all associated data is all listed together, it becomes unreadable, therefore, the list of all fixtures only contains limited related information.

No matter which query is selected, the next fixture to be played is always listed first and so on from there. It performs this by taking a timestamp value based on the current time and compares this to timings related to fixtures and outputs data accordingly (IMP2).

# /data/current_results.py
Works in a similar way to current_fixture_list.py using timestamps to identify the latest result and print accordingly.

# /data/current_player_stats.py
Statistics can be viewed via typing the name or initials of the desired player at the initial user query. There is also a list squad option to view possible entries. Currently, this only contains statistics for the premier league only! (IMP3)

# Improve <-------------------------
Would be ideal to add a basic UI at some point - Android, Win, Linux etc. Program lacks 'real-world' application and this would definitely help.

IMP2: Add additional data that might be useful - e.g. international broadcast information.

IMP3: Add a method of refining results to include both national cup tournaments (F.A. & Carabao)

