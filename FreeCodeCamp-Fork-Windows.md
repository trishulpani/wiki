# How to clone and setup the Free Code Camp website on a Windows pc

This list works with the FreeCodeCamp site and have been tested on this [Angular tutorial](https://docs.angularjs.org/tutorial) as well. Setting up the dev environment on a Windows pc is easy although it will give a ton of errors first in the process. The important part is to correct these errors.

## Toolchain

1. [Git bash](https://msysgit.github.io/)
2. [Node.js](https://nodejs.org/)
3. [MongoDB](https://www.mongodb.org/downloads)
4. [Python 2.7.10](https://www.python.org/downloads/release/python-2710/)

Install the 4 downloaded prerequsites. When installing Python and Node it is important to check the option add to the path variable. The Node installer does that by default. It is optional to add Mongo to the path. Python should be installed in a subfolder in %programfiles%

1. Open a command prompt with admin rights
2. Verify that Node is in th path with node -v
3. Verify that npm is in the path with npm -v
4. Do the following:

  ```bash
  npm install npm -g
  npm install bower -g
  npm install gulp -g
  npm install node-gyp -g
  npm install babel -g`
  ```

5. Private Environment Variables (API Keys)

    ```bash
    Create a copy of the "sample.env" and name it as ".env".
    Populate it with the necessary API keys and secrets.
    ```

    Edit your .env file and modify the API keys only for services that you will use.
    Note : Not all keys are required, to run the app locally, however MONGOHQ_URL is the most important one.

    If you only use email login, in addition to MONGOHQ_URL, SESSION_SECRET, add the MANDRILL_USER and
    MANDRILL_PASSWORD API Keys. Not setting these keys will throw an exception when you sign up which you can
    ignore, you will still be able to login, however you may get these keys [here](https://www.mandrill.com/signup/). Sign up and create a new pair
    of keys.

    You can leave the other keys as they are. Keep in mind if you want to use more services you'll have to get 
    your own API keys for those services and edit those entries accordingly in the .env file.


6.  If you want to spare the time in explorer finding Mongo when it has to be started create a `.cmd` file on your desktop and write the path to Mongo. Probably `%programfiles%\MongoDB\Server\3.0\bin\mongod.exe`.

7. Create the default folder for mongo to store databases: `C:\data\db`

**Every command from now on has to be executed from Git Bash. npm install and bower install is downloading components from Git repos and MUST have access to the Git commands**

1. Follow the instructions here [**FreeCodeCamp on Github**](https://github.com/FreeCodeCamp/freecodecamp) and clone the project.
2. Run `npm install` This will produce some warnings and maybe some errors. The warnings and some of the errors can be disregarded. Stackoverflow has large resources to solve the errors if they still come up the 2\. time you run npm install.
3. Run `bower install`, `npm install` again and `bower install`again
4. Start mongo from the desktop shortcut and run `node seed`. You should now see a lot of activity in the window where you started mongo.
5. Run `gulp` and note what port it starts the site on. (Should be 3000) Open localhost:3000 (or whatever port it started)

**You're good to go**
