# sqlalchemy-challenge

ReadMe SQL Alchemy
# Once the session was created, I wanted to get a sense of what kind of tables I was working with. So I used the inspector to collect the column name and type for both tables.

inspector = inspect(engine)
columns = inspector.get_columns('Measurement')
for c in columns:
    print(c['name'], c["type"])

inspector = inspect(engine)
columns = inspector.get_columns('Station')
for c in columns:
    print(c['name'], c["type"])


—————————————————————————————————————————————————
# Exploratory Climate Analysis #

# Design a query to retrieve the last 12 months of precipitation data and plot the results. I broke this task into four steps:
1. Design a query to retrieve the last 12 months of precipitation data
2. Upload query data to dataframe and name columns
3. Clean dataframe and order values by date
4. Plot precipitation data


# Calculate the date 1 year ago from the last data point in the database
I collected the last date from a previous query, which used date.desc().first(). This returned a row object. In the Ins.Dates lesson we learned how to use dt.timedelta to get query for elapsed dates. I wanted to convert that row to number, but didn’t find a solution quickly enough. So, I hand coded the date returned by date query. Since timedelta does not use years or months, used days = 365.


# Perform a query to retrieve the data and precipitation scores
# Save the query results as a Pandas DataFrame and set the index to the date column
# Sort the dataframe by date
# Use Pandas Plotting with Matplotlib to plot the data

These instructions in the starter and README really begin to diverge here. After consulting classmates and Felipe (TA), I request a fresh copy of the starter code and decide to complete the HW using the starter code instructions exclusively. After a confirming with AskBCS that these would return the same data and visual, I scrapped these cells. 



# Use Pandas to calcualte the summary statistics for the precipitation data
This came down to .agg or .describe. After reading documentation (which I find myself doing more and more of), .describe covered this requirement summarily.

—————————————————————————————————————————————————

# Design a query to show how many stations are available in this dataset?
Following a session.query that looked into the Station table, I implemented a len() to get 9. 


# What are the most active stations? (i.e. what stations have the most rows)?
# List the stations and the counts in descending order.
Most valuable query in terms of learning. Multiple elements, critical syntax, and ordering. The most valuable lesson was recognizing that I had to order_by(func.count(Measurement.station).desc()) to get the list in the correct desc order.


# Using the station id from the previous query, calculate the lowest temperature recorded, 
# highest temperature recorded, and average temperature of the most active station?
A case of overthinking it. Most of the code to solve this was laid out above. Just needed to try func.max and func.avg. Working to be a more efficient and fail-fast problem solver. 


# Choose the station with the highest number of temperature observations.
# Query the last 12 months of temperature observation data for this station and plot the results as a histogram
For this, I created a query based on the "last 12 months" info from earlier and added a filter for the most active station. Then, I converted this information into a DataFrame and found a simple histogram code via Matplotlib documentation.

# BIG THANKS
AskBCS for the clutch solutions
Sean (Instructor) for the flexibility and patience
The folks at StackO for sharing their work
Erika (partner) for the time and encouragement
