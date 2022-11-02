# CS5200-Practicum1

This private repository contains (Design and Implementation of a Relational Database: Bird Strike Incidents)

Tasks:

1)  (20 pts / 2.5 hrs) Inspecting the data file; assume that this database will be used for an app that can be used by pilots (of any kind of aircraft) to report wildlife incidents. Create a new database and connect to it from R. Then create the following database schema:

A)  Create a table that stores wildlife strike incidents called incidents(rid, date, origin, airline, aircraft, flightPhase, altitude, conditions, warning). Only store the date, not the time of the incident. Make 'warning' a Boolean flag and use TRUE if the pilot was warned, FALSE otherwise. Use appropriate data types and store the date as a date type not as text subject to the data types your chosen database supports. If date or boolean are not supported, choose another data type that will work or split the dates into month, day, and year columns.

B)  Create a table that stores airports and states called airports(aid, airportName, airportCode, state). aid is a synthetic primary key, airportName and state are the airport name and state from the data file. The airport code should be the airport's international code, e.g., BOS for Boston or LGA for LaGuardia. However, you may leave it empty for this database -- it is for future expansion.

C)  Link the incidents and airports tables via the origin foreign key in incidents to the primary key aid in airports. 

D)  Create a lookup table conditions(cid, condition, explanation) and link this lookup table to the incidents table with the conditions foreign key. This table contains the value of all conditions, e.g., 'Overcast'. Leave the explanation column empty (future expansion).

E)  Harmonize the flight phases to be one of: takeoff, landing, inflight, unknown. For example, for row 14, the flight phase was provided as "Landing Roll" -- change that to "landing" when storing the flightPhase. Code 'approach' as 'landing'; code 'climb' as 'takeoff', etc. Use your judgement as to what the appropriate harmonization is.

F)  Assume "Business" to be an airline name.

G)  Remove all military flights from the database.

H)  You may either use {sql} code chunks or calls to R functions to execute the SQL statements. 

2)  (25 pts / 5 hrs) 25 pts / 5 hrs) Place the Bird Strikes CSV file into the same folder as your R Notebook and the load it into R without a path name. The default path is the local folder that contains the R Notebook when you have the R Notebook in an R Project. Once loaded, populate the tables with the data from the appropriate columns. Omit the columns from the CSV that are not referenced in the tables.

Use default values where the data file does not contain values or leave empty. Records (rows) from the CSV that do not have flight information may be omitted. If there is no airport or airline, then link to a "sentinel" airline or airport, i.e., add an "unknown" airline and airport to the tables rather than leaving the value NULL. Assign synthetic key values as and where needed and use them as primary keys.

3)  (5 pts / 1 hr) Show that the loading of the data worked by displaying parts of each table (do not show the entire tables).  Document and explain your decisions. See the Hints below for information on db4free. All data manipulation and importing work must occur in R. You may not modify the original data outside of R -- that would not be reproducible work. It may be helpful to create a subset of the data for development and testing as the full file is quite large and takes time to load.

4)  (10 pts / 1 hr) Create a SQL query against your database to find the top-10 airlines with the most number of incidents. You may either use a {sql} code chunk or an R function to execute the query. It must be a single query.

5)  (10 pts / 1 hr) Create a SQL query against your database to find the flight phase that had an above average number bird strike incidents (during any flight phase). You may either use a {sql} code chunk or an R function to execute the query. It must be a single query. 

6)  (10 pts / 1 hr) Create a SQL query against your database to find the maximum number of bird strike incidents by month (across all years). Include all airlines and all flights. You may either use a {sql} code chunk or an R function to execute the query. It must be a single query. This query can help answer the question which month, historically, is the most dangerous for bird strikes.

7)  (5 pts / 4 hrs) Build a column chart that visualizes the number of bird strikes incidents per year from 2005 to 2011. Adorn the graph with appropriate axis labels, titles, legend, data labels, etc.

8)  (15 pts / 3 hrs) Create a stored procedure in MySQL (note that if you used SQLite, then you cannot complete this step) that adds a new incident to the database. You may decide what you need to pass to the stored procedure to add a bird strike incident and you must account for there being potentially a new airport. After insertion, show (in R) that your procedure worked. Note that if you used SQLite rather than the required MySQL for the practicum, then you cannot complete this question as SQLite does not support stored procedures.
