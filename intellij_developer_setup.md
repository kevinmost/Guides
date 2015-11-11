# Restline Wiki

### Clone the repository

From a terminal: `git clone git@github.com:Lifars/RestLine.git`

### Import the project in IntelliJ

_Note: All testing was done on IntelliJ 15. Procedures have been the same since IntelliJ 13 and are likely to stay the same for a very long time, maybe with the exception of slight wording changes_

1) Open IntelliJ and press "Import Project". Select the `pom.xml` in the root of your RestLine folder.

2) On the next page, check off "Search for projects recursively", "Import Maven projects automatically", "Sources", and "Documentation".

3) Keep clicking through with "Next" until finished.

### Configure environment variables when running in IntelliJ

IntelliJ lets us create custom run-configurations. We will set up one that launches our RestLine server (via the main method in `Restline.java`), and bundles environment variables that 

1) Open `Restline.java`

2) Find `public static void main` in this file. Right-click `main` and select "Create 'Restline.main()'...'

3) In the upper right corner of this dialog, check off "Single instance only"

4) Click the "..." next to "Environment Variables" and add the following:
_Note: for variables that you need to get off Heroku, refer to: https://dashboard.heroku.com/apps/restline/settings_
  - PORT: 4567
  - POSTGRES_USERNAME: [get from Heroku]
  - POSTGRES_PASSWORD: [get from Heroku]
  - POSTGRES_HOST: [get from Heroku]
  - POSTGRES_DB_NAME: [get from Heroku]

5) Apply changes and hit OK. To return to this config screen, press the dropdown next to the "Run" button in the upper right corner of IntelliJ.

### Create a database in IntelliJ

1) Along the right edge of IntelliJ should be a "Databases" button. Click it to open the Databases pane. _Note: If this button is not along the edge of your window, go to View -> Tool Buttons and it should appear_

2) Click the + button, then "Data source from URL"

3) In the text box, enter `jdbc:postgresql://[POSTGRES_HOST]:5432/[POSTGRES_DB_NAME]?user=[POSTGRES_USERNAME]&password=[POSTGRES_PASSWORD]&ssl=true&sslfactory=org.postgresql.ssl.NonValidatingFactory`, replacing all of the variables in `[BRACKETS]` with their values from the Heroku environment variable config page. _Note: The value in Heroku for `POSTGRES_HOST` may have a slash at the end of it. Remove that slash from what you enter in the text box!_

4) Ensure that the dropdown below the text-box is set to PostgreSQL (it probably is if you configured your URL correctly above)

5) Press OK, and you should be brought to a new page. At the bottom, there might be a yellow triangle with a message prompting you to click "Download" to install the Postgres drivers. Do so.

6) Press "Test connection" and ensure the message is successful.

7) Switch to the "schemas" tab and uncheck everything the `[DB_NAME].public` entry (which should be the last one in the list).

8) Press OK

You should now be able to run RestLine in IntelliJ by making sure that you have the proper run-configuration set in the dropdown in the upper-right corner of IntelliJ, and then pressing the green arrow.
