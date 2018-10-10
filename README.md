# Uploadly

## Description

This is a SPA where users can view documents and admins can upload them.

## User Stories

-  **404:** As an anon/user I want to see a 404 page if I try to reach a page that does not exist so that I know it's my fault.
-  **Create users:** As an admin I want to create users and give them access rights.
-  **Login:** As a user/admin I want to login to the platform so that I can see my documents.
-  **Logout:** As a user I want logout from the platform so no one else can see my documents.
-  **Upload documents** As an admin I want to upload and preview documents assigned to a user.
-  **Profile** As a user I want to see what documents I have in my profile and know when did I received the document.
-  **Give feedback** As a user I want to give feedback on the documents before returning them to admin.
-  **See the app description** Additionally as a user I want to see a description of the uses of the app.
-  **Delete documents** As an admin I want to delete document if theres a wrong file upload.
-  **Delete users** As an admin I want to delete users so the database is up to date.


## Backlog

Update documents

Emails:
- receive new user notification

File upload from users:
- Upload files with modifications

Search bar:
- Search for documents

Notifications:
- Receive notifications when there's a new comment.
- Posting comments/feedback (users)
- Receiving notification of commects (admin)
- Reply to the comments (admin/user)
- Display the threads
- Limit the threads
- "See more"
  
# Client

> Admin
## Routes

- / - Homepage
- /auth/login - Login form
- /user/create - users list
- /user - users list
- /user/profile - user document list
- /user/:id/delete - delete user
- /document - documents list
- /document/create - documents create
- /document/detail - document detail 
- /document/:id/delete - delete document

> User
## Routes

- / - Homepage
- /auth/login - Login form
- /document - document list (that belong to me)
- /document/detail - document detail 
- /profile/me - my documents - @toask (Should this be by id and not /me so admins can access?)
- 404

## Pages

- Home Page (public)
- Log in Page (anon only)
- User Create (admin only)
- Profile Page (user only)
- Document List Page (admin , users)
- User List Page (admin)
- 404 Page (public)

## Components

- User Card component
  - Input: user: any
  - Output: last login, users name, number of documents.
- Document component
  - Output: document(title: string, type: string, last update date, own of uploading )

## IO


## Services

- Auth Service
  - auth.login(user)
  - auth.signup(user)
  - auth.logout()
  - auth.me()
  - auth.getUser() // synchronous
- Document Service
  - document.list()
  - document.create(data)
  - document.detail(id)
  - document.removeDocument(id)   
- User Service
  - user.list()
  - user.create(data)
  - user.profile(id)
  - user.removeUser(id)

# Server

## Models

User model

```
username - String // required
password - String // required
role - String [enum: 'admin', 'user']
lastLogin - timestamp
```

Document model

```
recipient - ObjectID<User> // required
uploadedBy - ObjectID<User> // required // default : currentUser
name - String // required
type - String [enum: 'contract', 'proposal', 'presentation', 'survey']
lastUpdate - date
```

## API Endpoints/Backend Routes

- GET /
- GET /auth/me - @toask (related to question above on id vs me)
- POST /auth/login
  - body:
    - username
    - password
- POST /auth/logout
  - body: (empty)
- POST /user/create
 - body:
    - username
    - password
- GET /user
- GET /user/:id/profile
- DELETE /user/:id
  - body: (empty)
- GET /document
- POST /document/create
  - body:
    - name
    - recipient
    - type
    - lastUpdate
    - uploadedBy
- GET /document/:id
- DELETE /document/:id


## Links

### Trello/Kanban

[Link to your trello board](https://trello.com) or picture of your physical board

### Git

The url to your repository and to your deployed project

[Client repository Link](http://github.com)
[Server repository Link](http://github.com)

[Deploy Link](http://heroku.com)

### Slides

The url to your presentation slides

[Slides Link](http://slides.com)