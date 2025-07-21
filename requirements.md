## High level Objective 

To build a React JS application to
- plan my workout routines
- create workout schedule by using my workout routines 
- log my workouts
- visualize the progress

## Functional requirements
Below is the detailed requirement specification for this application. The specification is predominantly written from an end user's perspective, giving them the shoes of a Product Owner.

### Planning workouts
This section deals with the capability of a user to plan their workouts by creating workout routines, creating workout schedules and applying the routines in the schedules

As a user I would like to create one or more workout routines
    - For each workout routine that I create , I would like to specify a name
    - For each workout routine that I create,  I would like to define the composition of my workout routine by
        - Choosing which type of workouts I am going to cover as part of the routine
            - I would like the workouts to be categorized as Strength or Cardio
            - A routine could be composed of strength training workouts or cardio workouts or a mix of both 
        - Pick and choose each workout that I would like to do as part of the routine
            - Each workout has to be represented by its name and a small svg image that is the symbolic representation of the workout
            - There should be a pre-populated expansive list of well known workouts, each with its name and an svg representing the workout. Some samples include Bench press, Treadmill run, Jump rope etc.
            - From this list, I should be able to select workouts to make up a routine
        - For each workout, define the intensity and/or the duration
            - Intensity can be specified in terms of  
                - weights (in Kilogram or Pound), reps and sets for strength training
                - level for cardio workouts such as treadmill, cycling etc
            - Duration can be specified in terms of 
                - minutes
            - Workouts can have intensity, duration or both, so I , as a user can specify either intensity or duration for each workout

As a user I would like to modify or delete my workout routines
    - When a workout routine is modified, the changes should apply to all future, un-logged workouts in the schedule. Past, logged workouts should remain unchanged.

As a user I would like to create my recurring workout schedule by selecting
    - The number of days in a week that I would like to workout
    - The time of the day in which I prefer to workout
    - For each day that I plan to workout in a week, I would like to apply one of my workout routines that I created
        - i.e. If I had chosen to workout 3 days a week, I need to select my routine for day 1, 2 and 3

### Logging workouts

As a user, I would like to log one or more workout sessions in a day

As a user, If I have a workout schedule created along with the workout routines, I would like to log a workout session for a day against the routine as per my schedule
    - I would like to log if I had worked out on a particular day
    - I would like to log which workout routine I followed on a particular day
        - If I select a routine, I should be able to log the intensity and/or duration in many ways
            - I can choose to log the same intensity and duration that I set as part of the routine. If I had worked out with the same intensity and duration as configured in the routine, this would be a rapid way to log my workout session, as I would be just clicking a single button to do this.
            - If I had worked out with a different intensity or duration, I should be able to log those different values against each workout in the routine.
            - I should be able to log a subset of workouts specified in the routine. 
            - I should also be able to log a workout in addition to those that are specified in the routine
    - I would also like to log workouts even if I don't follow any preconfigured routines
        - I should be able to select workouts and log intensity and/or duration for each workouts
        - I should also be able to create a new routine out of the logged workouts, intensity and duration on a particular day, and save it, which could be used in my schedule or reused for another day.
    - I would like to see all my logged daily workouts in detail in a screen in the app

As a user, I would like to edit a logged workout session by adding, modifying or deleting workouts in that session

As a user, I would like to log the state of my mind after the workout session. These are predefined states and could be like happy, content, calm, exhausted, frustrated etc.

### Monitoring Progress

As a user, I would like to continuously monitor my progress with respect to my workouts, routines and schedules in the application.
- Though workouts are driven by routines, I would like the log data to be avaible for each individual workout level, so that they could be aggregated for new usecases
- I would like to look at the tragectory of the intensity and duration of the workouts in a graph for each workout, over a period of time
    - What is the intensity of a workout in terms of total volume per day/week
        - Volume = Weight x reps x sets
    - What is the total duration of a workout over a day/week
    - i.e. For each workout, I would like to have stats graphed per day/week
- I would like to see graphical stats like
    - How many days did I workout per week/month
    - How many hours did I spend working out per week/month
    - Which routine is being followed by me the most per week/month

### Data Export and Import

- As a user, I would like the ability to export all my data (routines, schedules, workout logs) in a zip file
    - The data format should be csv or json and I should be able to choose the same
        - Schema for each workout in csv format:
            - date, routine, workout, workout_type (strength/cardio), weight, sets, reps, duration, mood  
        - Schema for each routine in csv format:
            - each entry in the csv represents a workout which would have routine name, workout, workout_type (strength/cardio), weight, sets, reps, duration
        - Schema for workout schedule in csv format:
            - schedule_name, number of days covered in the schedule, list of routines where each routine would map against a particular day
        - The JSON format would also have the same schema
    - There should be separate files for routines, schedules and workout logs

- As a user, I would like to import data from a zip into the application. This zip has to have the same format (same data formats for files within the zip) of the export zip archive, specified in the previous step.
    - In case of conflict in the names of workout logs, routines or schedules, confirm with the user to either overwrite or rename the entity before importing

### User account management
- Users should be able to signup/login using their Google account (social login). 

## Technical Requirements

- Frontend - React JS
- Backend - Node JS with express.js
- Database - MongoDB - I prefer a NoSQL for this application
- Containerize the application with docker and docker-compose so that I could run and test it locally

### Non functional requirements
- Make the frontend app as completely grayscale themed. No colours
- Use MUI for frontend design
- Make the frontend design as mobile-first and extremely responsive
- Build the frontend app as a Progressive Web App
    - The application must support offline functionality. The user should be able to create, view, and log workouts while offline. All changes made offline must be synced with the server automatically when the connection is restored
- User data needs to be persisted in the database and should be accessible across all devices
- Choose an apt and unique name for my application so that I can publish it