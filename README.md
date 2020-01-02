# project-3-the-scoop
Project 3 for Codecademy API intensive

## Project Overview
The Scoop allows users to:
* Create and log in to custom username handles
* Submit, edit, and delete articles containing a link and description
* Upvote and downvote articles
* Create, edit, and delete comments on articles
* Upvote and downvote comments
* View all of a user's articles and comments

## How to Begin
To start your server, run npm install and then node server.js from the root directory of this project. Every time you change server.js, you will have to restart your server before the changes will take effect. To do this press "control + c" in the bash terminal where your server is running (or close the terminal) to shut it down and then re-run node server.js to start it again. While your server is running, you will not be able to run commands in the bash terminal, so open a new terminal if you want to run other commands.

To view your local version of the site, open index.html in Google Chrome. 

Note: When adding an article to the Scoop, you will need to add https:// to the beginning of your url.

## Route Paths and Functionality
### /comments

* POST
  * Receives comment information from comment property of request body
  * Creates new comment and adds it to database, returns a 201 response with comment on comment property of response body
  * If body isn't supplied, user with supplied username doesn't exist, or article with supplied article ID doesn't exist, returns a 400 response

### /comments/:id

* PUT
  * Receives comment ID from URL parameter and updated comment from comment property of request body
  * Updates body of corresponding comment in database, returns a 200 response with the updated comment on comment property of the response body
  * If comment with given ID does not exist, returns 404 response
  * If no ID or updated comment is supplied, returns 200 response

* DELETE
  * Receives comment ID from URL parameter
  * Deletes comment from database and removes all references to its ID from corresponding user and article models, returns 204 response
  * If no ID is supplied or comment with supplied ID doesn't exist, returns 400 response

### /comments/:id/upvote

* PUT
 * Receives comment ID from URL parameter and username from username property of request body
  * Adds supplied username to upvotedBy of corresponding comment if user hasn't already upvoted the comment, removes username from downvotedBy if that user had previously downvoted the comment, returns 200 response with comment on comment property of response body
  * If no ID is supplied, comment with supplied ID doesn't exist, or user with supplied username doesn't exist, returns 400 response

### /comments/:id/downvote

* PUT
  * Receives comment ID from URL parameter and username from username property of request body
  * Adds supplied username to downvotedBy of corresponding comment if user hasn't already downvoted the comment, remove username from upvotedBy if that user had previously upvoted the comment, returns 200 response with comment on comment property of response body
  * If no ID is supplied, comment with supplied ID doesn't exist, or user with supplied username doesn't exist, returns 400 response
