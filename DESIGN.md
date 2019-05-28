# Design Document - DESIGN.md

We decided to create our website as a Flask app because it was what we had the most experience with. Additionally, we knew that because we did not have to learn as many new techniques as if we had made an iOS app, we would be able to implement more functionality into our website which we saw as more important. We ultimately knew that we wanted to add as many features to our website as possible, and this format allowed us to do that.

## Using Finance
We ultimately began by copying over our code from finance and stripping out the finance specific code so that we had a blank website set up with register and login forms already completed via the previous psets. We also made the decision to utilize the error.html page from problem set 7 to display errors because we thought it looked the most professional and was the easiest to use. After having this initial framework for the website, we began to discover what specific functionality we need to add and how to accomplish it.

## Google calendar API
A lot of describing what the actual code is doing is in our comments around the code. However, there are a couple things that were extremely central to our project. We knew that a lot of the functionality we wanted to do with displaying a calendar could be accomplished via Google Calendar, so we decided knew that was something we needed to figure out. Ultimately, discovering how to use Google Calendar gave us the opportunity to display events in a calendar format, allow user to add events to their own calendar, and allow users to get directions via Google Maps to the event. The Google Calendar API was very central to the design of various features of our website.

## SQLite databases
However, even more central to our project were our SQLite databases. We knew that creating these databases and working with the information in them would be the most fundamental feature of our website. We took a lot of time to determine what tables we would need, what columns those tables would need, and what type the columns should be. In our events table, a lot of the columns ended up being of the type text because we did not want to limit the amount of information users could input or have the database accidentally cut off vital information. Our users table had more columns which could be specific types rather than just text, so we utilized those where they were appropriate. In the clubs table, a lot of the columns were also text because we scraped the data from the Student Organization List on the Dean of Students Office’s website and did not want data to be cut off. Because there are so many student organizations that are a part of the college and we didn’t want to have to copy over the information by hand, we used BeautifulSoup and requests to quickly scrape the relevant information (name, email, category, and purpose) from the Student Organization List and populate the clubs table.  Another design decision we made with the events database was using a foreign key to store the club id rather than storing the entire club name.

## Designing the website
We also wanted to make a visually appealing website, which we accomplished with our CSS and HTML files. We utilized Bootstrap a lot in designing our web pages because we liked how Bootstrap had improved our previous psets, especially finance and survey. Bootstrap was primarily used for displaying the events and clubs, as well as formatting all of the forms in our website. We also did some of our own styling via the CSS file such as adding a background image and changing font color.

## Uploading images
Another design decision we made, for simplicity, was how to upload and display photos via our website. Here, Flask was again extremely beneficial to us because saving photos via the upload folder configuration of flask was fairly simple compared to other options. We then made the decision to display that image by storing the path to it in the database and linking that path in the html page itself. We found this to be the easiest way to “store” images in the SQLite database.

## Storing multiple items in database within one entry
We also had to determine how to store lists in the database. We knew that users might need permissions for multiple clubs, would want to subscribe to multiple clubs, and might want to indicate multiple preferences. We didn’t want to have multiple duplicate rows, so we ultimately decided to store these as a comma separated strings and then split that string into a list at each of the commas when we need to access the individuals elements. We found this method to be the easiest for us, because it allowed us to dynamically update user preferences using python’s list methods.

## Helpers
We chose to abstract away the aforementioned list handling into helper functions ```parse()``` and ```rejoin()``` in ```helpers.py```. We also created a send email function in helpers.