# BMart

## About
BMart is a full-stack JavaScript project built upon [React](https://reactjs.org/) and [GraphQL](https://graphql.org/). It is an app that is designed to be an online grocery store. However, since the administrator is able to update what items can be sold this site can be used as a base for any store who would like to use this particular site makeup. It is built primarily with React and [Apollo](https://www.apollographql.com/docs/react/) on the client side, with GraphQL Yoga amd [Prisma](https://www.prisma.io/) connected on the backend.

Currently the administrator can add items, delete items, and edit items. Customers can add items and remove items from their cart. Updating address input, cleaning up permissions issues, and adding user account functionality are planned features for the next sprint. As the app development progress, the styling will be updated to become more uniform accross the entire app. This app is still very much in the developmental phase. I welcome feedback and suggestions.

## Tech
 * [Node](https://nodejs.org/en/)
 * [React](https://reactjs.org/) 
 * [Apollo](https://www.apollographql.com/docs/react/) 
 * [GraphQL](https://graphql.org/)
 * [Prisma](https://www.prisma.io/)

## Installation

### Install Dependencies

Make sure you have [Node.js](https://github.com/nodejs/node) and Prisma installed.

Download and install dependencies.

```
git clone git@github.com:darccide/BMart # or clone your own fork
cd BMart
<!-- Be sure to install dependencies in both frontend and backend folders -->
cd frontend
npm install
cd backend
npm install
```

Prisma Setup

Make sure that you connect your app to a database first. This one is connected to a Prisma test database, but you can connect it to your own SQL database by following the directions at Prisma. Below is a guide to set up your own Prisma Database.

### Backend

Make sure you are working in the backend folder of the BMart project:

`cd backend`

First you need to install the Prisma CLI:

`npm install -g prisma`

After that you may need to login which can be done by using:

`prisma login`

Next you need to initialize the database by using:

`prisma init`

Follow the prompts and I recommend using the `Demo Server` to test, but you may use any other DB that you want. Follow through with the rest of the steps by naming it and giving it the stage `dev`. You may also get a prompt asking for the Programming Language. For that you may set it to `Don't Generate`.

Your Prisma server should be set up. You now need to change the files a bit to work with our project.

**NOTE** - You may also delete or repurpose the datamodel.prisma file that was created, since the data model will be built using the datamodel.graphql. 

In the root directory of the backend folder be sure that you create and set up your own `variables.env` file with the following information:

```
cd backend
touch `variables.env`
```

Fill in the `variables.env` file with your own information. The `PRISMA_ENDPOINT` is found in the `prisma.yml` file:

```
FRONTEND_URL="http://localhost:7777"
PRISMA_ENDPOINT="YOUR PRISMA ENDPOINT HERE FROM PRISMA.YML FILE THAT WAS CREATED"
PRISMA_SECRET="MAKEUPYOUROWNSECRET"
PORT=4444
STRIPE_SECRET="PRIVATEKEYNEEDEDFORDEPLOY"
```

In the `prisma.yml` file be sure to include the following data:

```
# DEVELOPMENT ENDPOINT - PUT IN VARIABLES.ENV - UNCOMMENT FOR DEVELOPMENT / COMMENT OUT FOR PRODUCTION

endpoint: ${env:PRISMA_ENDPOINT}

# PRODUCTION ENDPOINT - USE YOUR OWN - UNCOMMENT OR REWRITE FOR PRODUCTION
#endpoint: YOUR OWN END POINT

datamodel: datamodel.graphql
secret: ${env:PRISMA_SECRET}
hooks:
  post-deploy:
    - graphql get-schema -p prisma
```

Finally, you can run the following to deploy the datamodel to the database at any time:

```
npm run deploy
```

Once the prisma database is set up you may run the development server with:

```
npm run dev
```

Your backend should now be running on [localhost:4444](localhost:4444).

### Frontend

Make sure your dependencies are installed in the frontend folder. You may then use:

```
npm run dev
```

Your app should now be visible on [localhost:7777](localhost:7777).

Make sure you are running both the frontend and backend folders.

## Author
Steven Thomson is a Fullstack Developer who recently transistioned back to the U.S. If you would like to contact him:

 * steven.thomson88@gmail.com
 * [Steven Thomson's LinkedIn](https://www.linkedin.com/in/steventhomson1988/)

