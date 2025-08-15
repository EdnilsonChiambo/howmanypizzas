# howmanypizzas

Determine how many pizzas to order for a meetup.

# The Problem

Imagine you are an organizer for a meetup or conference for your favorite programming language.
Among many other things, you are responsible for catering. Someone is going to ask you how many people will
attend so they can order food and beverages (e.g. pizza).

While you could order enough food for everyone that has registered, you know from experience there are
some difficulties and variables:

- You want to be as accurate as possible on the food and beverage orders. You don't want to waste food, but you 
don't want to run out either.
- Catering needs to be ordered a few days in advance.
- Not everyone that registers actually attends.
- Many people register the day before or even the day of.
- There are "walk-in" attendees.
- You're not clairvoyant nor have a magic crystal ball that can see into the future.

You do have access to real-time registration information. A few days before the meetup you can view it. 
But, armed with this information, how do you predict how many people will attend?

Fortunately, you also have access to historical data from prior meetups. You also have access to Python and 
lots of cool statistics, machine learning, and other libraries. You can write a Python program to take the 
prior datasets, and the current event registration data (for example, 3 days prior), to create an estimate 
of the number of expected attendees. You provide that number to catering, with confidence that you've used 
a sound approach (neither clairvoyance nor magic required).

# Event Data

Prior event data has already been gathered into CSV files in the `data` directory.

`sf_python_<event_date>.csv` has the registration data for the dates leading up to the event.

`checkins.csv` has the actual check-in data (i.e., how many people actually showed up to eat the pizza)

# The Challenge

Create a model that uses prior event data that, when given the data for the current event 3 days prior, 
predicts the number of expected attendees.

While you could provide a single number, it's best to also provide other statistical information. For example,
what is the confidence interval for a given confidence level?

# My Branch Implementation

This branch adds a the final dataset used for the problem and Jupyter notebook that:

Combines all past events with available check-in data into a single dataset, excluding the most recent event (reserved for testing).

Splits data into training and test sets to compare different models.

Evaluates multiple regression models, including:

Simple Linear Regression

RandomForestRegressor

GradientBoostingRegressor

XGBRegressor

Selects the best-performing model — GradientBoostingRegressor — which predicted 47 attendees for the last event (actual attendance was 48).

Implements bootstrap resampling with XGBRegressor to estimate a 95% confidence interval for predictions.

Evaluates performance using metrics such as MAE and R² 

# Future Improvements
Feature engineering for short-term trends, e.g.,

Visitors in the last 3 days

Registrations in the final week

% growth in registrations week-over-week

Ratio of registrations to visitors

Experiment with ensemble methods combining multiple models.

Incorporate external data such as weather or nearby events.
