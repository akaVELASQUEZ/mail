# Email
#### Video Demo:  N/A yet
#### Description: An Email Server Single Page web application made using Pythons Django Framework and Vanilla Javascript.
#


# Introduction
Good day everyone, this is Allan Kristoffer Velasquez and this is my submission for CS50w project 3. This is an email server single page web application made using django framework and vanilla javascript. My third django web application and my first SPA. Im still learning React.JS so this single page application is made by using vanilla javascript. This web application is fully web responsive using bootstrap, CSS grid and flex. 


# Code Structure
This Email web app is made using Django framework. The main app is the mail app where all the urls and views were located. The whole Backend of this application is made by CS50 team and only the Frontend was coded by me. Listed are the code structure for the FrontEnd of this Single Page Application

## Inbox.html
Inbox.html is the only html page in this application to that implements the whole email server application (excluding the login and register pages). It first loads everything in the layout.html which contains the stylesheets and some script tags. The first content of the inbox.html is the sidebar which contains the buttons or links for the other part of the application. Next would be the content area where all the contents of the application and nav bar(when on mobile) would show. Next are the containers for the functionalities of this email application. The div with emails_view that would show the email inbox, compose_view which shows a form for composing emails, and email that would show all the contents of an email. A search_view is also included in the page for a future feature of the page that would enable the user to search for an email.


## Inbox.js
The Inbox.js contains all the necessary javascript codes needed to implement the email web application. This single page application is made possible by changing the display style of the divs of the inbox.html page based on what page is clicked by the user. The first part of inbox.js is for implementing the transformation of the sidebar by toggling a classname to the sidebar. The next part before the functions are the one responsible for toggling between views. Clicking the nav items of the nav bar would call the functions for the certain view.

### compose_email function
Compose_email function is called when the user wants to create an email to be sent to other registered user. First it would change the display style of every other view to none and the compose_view to block. It would then remove every entry in the forms to empty the forms at the initial state. When the submit button is clicked, it would first prevent the page from reloading by calling prevent default. It would then fetch the contents of the email to the /emails route via post method. If the response is ok or with no errors, it would redirect the user to the sent view where the user will see the sent email. The settimeout function is used for the page to have time to fetch the sent emails data. The parameters of the compose_email function is used for the reply function to fill the value of the forms when the reply is clicked.

### load_mailbox function
This function is responsible for showing the mailbox of the user. The function gets a mailbox parameter to choose whether to show inbox, archived or sent mailbox. It would first fetch the data from /emails/mailbox route where mailbox is the parameter. The backend would filter the emails in the Email model and would send it as a response to the request. The response would then be looped using foreach to be able to show every email of the response. A button would be created for each emails that would call the archive_email function to archive the certain email and would change the email display style to none to remove the email to the mailbox. The whole div for email except the archive button could also act as a hyperlink for the email that would call the view_email function to show the email contents. 

### view_email
View email function is the one responsible for showing the view of the contents of the email. It would first change the display of other views to none. It would then make a PUT request to change the read of the email model to true. It would then fetch the email content to emails/email_id route and print it on the page. A reply button would be made to be able to reply to the email. When the button is clicked, it would call the compose_email view passing parameters based on the email.

### archive_email 
Archive email is a simple function responsible for toggling the archived data of the email model. It would fetch data from emails/email_id route and toggle the value of archived key. 