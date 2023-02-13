Heroku Parquet Corrections Proof of Concept
# Pardot data corrections by API for Heroku
This project will update the Pardot Country & State values from 2 letter abbreviations to full names. You can now turn on Pardot GeoIP and SFDC Country Picklists and not have all your prospects stuck in the Error Que. Pardot Prospects get the State or Country values updated every 10 minutes if needed.

It is designed to run on Heroku. A 'hobby' level Heroku account is enough to support this code.

This is based on the Pardot API sample code http://developer.pardot.com/#sample-code and the Heroku "Getting Started on Heroku with PHP" https://devcenter.heroku.com/articles/getting-started-with-php guide. 

Following the tenants of https://12factor.net/ the logins are stored in Heroku as Config Vars in the settings tab. They can also be used locally by setting them as ENV vars.
 * pardotLogin
 * pardotPassword
 * pardotUserKey

Reminder, the API user needs to be set to USA EAST COAST timezone - the same as the Pardot offices as there is a bug in the date/time calculations on the API.
Reminder, the Pardot API user needs to be set to USA EAST COAST timezone - the same as the Pardot offices as there is a bug in the date/time calculations on the API. It is recomended to create a new 'Marketing' user just for this tool so it's easy to identify when this tool has made changes to the data.

In Heroku resources, add the "Heroku Scheduler" add on and add a new job for every 10 minutes "php workers/CountryStateFixer.php".
