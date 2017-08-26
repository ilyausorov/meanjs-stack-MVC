# meanjs-stack-MVC
Reorganized the MEANJS.org repo into an easier to work with folder structure based on using MVC first. Hope this helps folks use the Mean stack more easily. Forked from mean.js 5.0.

Obviously full credit to the Meanjs team for this fantastic stack: https://github.com/meanjs/mean. See their page for full instructions.

The main goals for doing this were:
- organize folders according to the MVC pattern first, then by topic, rather than vice versa
- separate out backend into one set of folders, and client-side into another set of folders
- simplify some areas to have less files and folders such as routes, CSS, and everything to do with controller files

The folder structure I used is as follows:

1. app
    - routes
      - server.routes.js (keep all server routes in one file for simplicity)
    - sockets (all the stuff to do with sockets goes here so it can be indexed separately)
    - controllers
      - admin (I always keep admin files in a separate folder from core user files)
      - core
      - social_login (the various social login strategies. make sure you set up your app id's and keys in settings)
      - articles
      - users
    - models
      - article
      - user
    - views
      - views_html
        - admin
        - articles
        - authentication
        - basic_layout (these are the templates that are compiled server side so they are in the Handlebars.js format)
        - core
        - email templates
        - password
        - settings
      - views_javascript (I also use MVC-first on the client-side)
        - controllers (the "*.client.module.js"files and the config.js and init.js; loaded first)
          - admin
            - articles
            - core (also contains the defintions for the various custom directives, page title, errors and other core info)
            - users
          - articles (each folder contains the main controller file, the menus file and the routes file)
          - chat
          - core
          - users
        - models (client side models call the server side controllers)
          - articles
          - core
          - users
2. public
    - css (just one css file for simplicity, not a fan of all the CSS pre-compiling)
    - fonts
    - images
    - libraries (all your angular files)
3. settings
    - common_files (the base express.js, node.js and mongo db files)
    - environment_settings (this is where you have to add your database details, social login app id & key and other details)
    - file_import_settings (try not to mess with this unless you're changing the folder structure again)
4. misc (assorted files for deploy, testing, and scripts)
  
  
# Getting Started
1. Download the repository onto your computer, preferably as close as possible to your root (~/[your-name] on Mac or C:/Users/[your-name] on Windows) directory
2. Go to mLab, make an account and create a new MongoDB data in sandbox mode. Click it and copy the URL that they give you. It should look something like this: mongodb://\<dbuser>:\<dbpassword>@ds152363.mlab.com:56323/[database-name]
3. use the terminal on Mac or command prompt on windows to navigate to the folder where you downloaded the repository and use the npm install command. This requires that you have already installed node.js and npm.
4. Go into your settings/environment_settings/development.js file and update line 7 with the url of your MongoDB database. It should be in single quotes, kind of like this: uri: 'mongodb://\<dbuser>:\<dbpassword>@ds152363.mlab.com:56323/[database-name]'. Make sure you actually replace the username and password fields with your actual username and password.
5. In your terminal or command prompt, use the npm start command to start the app.
6. Navigate your browser to http://localhost:3000 to start the app. Make sure you always code with your Dev tools open.

Cheers-
