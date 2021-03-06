# Ibank

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 10.1.7.

## Run, app, run!

To start a local instance of the application, do the following in bash or a similar shell.

```bash
#!bin/bash
git clone <repo-name>
git checkout develop
npm install
ng serve
```

PS: This requires that

- [NodeJS](https://nodejs.org)
- [Angular CLI](https://cli.angular.io/)

be installed on your machine

## Overview

### Features

The ibank app is a web-based service designed for the management of one's bank account. It will allow users to

- view their account balance
- view their account statement, presented as a history of trasnsactions
- send money to other accounts in the same bank
- send money to any mobile number (mimic withdrawal)

### Security

To access their account, users need to be authenticated.

The app manages user authentication using a third party identity as a service provider, namely [Auth0](https://auth0.com).

With Auth0, users can login using

- an email and password combination
- social login via providers like Google

On sign in/up, Auth0 sends the user profile back to the app. The profile includes the user's email address, which matches the email address tied to their account.
The record of transactions for this user is then retrieved.
A user must confirm ownership of an email address by clicking on a verification link sent to the email address on login, or by entering a verification code.

### Data Models

#### Note
The bank end is developed in a separate repo (link coming soon).

The app achieves data persistence using a MySQL database.
It has tables for Users, Transactions and Accounts.

A Transaction is the most basic record in the database. It is defined by the fields:

- `transaction_id`: an autogenerated value used as the record's primary key
- `user_id`: transactor primary key
- `transaction_title`: a short textual description of the transaction
- `amount`: the amount of money involved in the transaction
- `timestamp`: a datetime record of when the transaction was made/recorded

### Feature Components

#### Home

Defines the site's landing page. Redirects to user's dashboard on successful authentication.

#### Transactions

Defines the transactions view. The default view is a table of transactions.

Each transaction includes a link to a page with a more detailed view of the transaction.

### (External/Other) Modules

The app employs these external libraries to achieve styling:

- [Bootstrap-v4](https://https://getbootstrap.com/)
- [Material UI](https://material.angular.io/)

### Unit testing

WIP

### End-to-end testing

WIP


### TODO (Roadmap)

- implement 2fa properly. Consider using AT's API to send SMS on login, and also using an Authenticator App
- complete feature list as described in `will allow user to` above.
- add more features in the app (analytics on accounts, capacity to add multiple accounts from different banks by plugging in those banks' APIs, capacity to plug in Mpesa using the Mpesa API, etc)
