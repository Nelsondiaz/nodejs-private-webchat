nodejs-private-webchat
======================

Hosting the chat on Heroku

Heroku is a cloud hosting platform that automates the deployment and scaling of web apps. It offers a free plan, which is sufficient for less busy apps like our chat. Here is what you need to do:

Create an account, if you don’t have one already.
Install the heroku toolbelt for your operating system. It will give you access to the heroku command from a terminal window.
Initialize an empty git repository (explained below)
Push your code to heroku. This will deploy it and give you a URL which you can share with your friends.
You can also read this getting started guide, followed by this guide about running node.js applications.

Creating a git repo

The heroku toolbelt installs the heroku command and the git version control system. You need to create a git repo in order to be able to deploy your app to heroku (there is no ftp here). To do this, run this command:

git init
Then, we need to tell git not to include the node_modules folder to your repo. This folder can grow quite large and it simply does not belong in git. To ignore the folder, create a new empty text file named .gitignore with the following content:

node_modules/
Now you can commit your code to your fresh new repo! Write these commands:

git add .
git commit -m 'Initial commit'
There is one last thing that we have to do. Heroku requires that your application has a text file named Procfile, which contains the command used to start your node.js app. Create it, and add the following content:

web: node app.js
Then commit the changes with these commands:

git add Procfile
git commit -m 'Added a procfile'
We are now ready to push the application to heroku!

Pushing to Heroku

The following two commands are only done the first time you start using the heroku utility. First you need to login to heroku from the command line tool:

heroku login
Then, you need to add your ssh key, so you can push code without entering a password:

heroku keys:add
Next, you need to create a new heroku application from the code in this folder:

heroku create
And finally, we are ready to push code! Type this command:

git push heroku master
This line will send your application code to heroku, where their servers will process your package.json file and install all libraries that your app needs. Do this every time you need to upload a new version of the code (you must have made a commit beforehand). All that is left, is to enable websockets so that our real-time chat can work (read more here):

heroku labs:enable websockets
To open your very own web chat in your browser run this command:

heroku open
This will open it in a tab in your default browser.

Hope you like our little chat!

But there is much more that can be improved on it. You may implement alerts of new messages with HTML5 audio, make it possible for more than two people to join the same room, to require passwords before joining and more. If you make something cool, be sure to share it in the comments for everybody to see :)
