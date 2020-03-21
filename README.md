Status: Not quite finished, cleaning it up, messy/quick&dirty

Basically two files are important (as well as config files):
- controllers/coronacampus/Cli.php
- libraries/coronacampus/Appbase.php

1. Create to elastic search indexes:
a) coronocampus
b) coronacampus-test

2. Create config files for API access:

/config/development/appbase.php

```
// production
$config['appbase_auth_string_read_coronacampus'] = "zvF51XXXb:cf198494-177dXXXX";
$config['appbase_auth_string_write_coronacampus'] = "nBYXX4sq:889738e4-56b5-XXXX";
$config['appbase_app_name_coronacampus-test'] = 'coronacampus-test';
$config['appbase_api_url_coronacampus-test'] = 'https://scalr.api.appbase.io';
// test
$config['appbase_auth_string_read_coronacampus-test'] = "zvFXXb:cf198494-177dXXXX";
$config['appbase_auth_string_write_coronacampus-test'] = "nBY9864sq:889738e4-56b5-XXXX";
$config['appbase_app_name_coronacampus-test'] = 'coronacampus-test';
$config['appbase_api_url_coronacampus-test'] = 'https://scalr.api.appbase.io';
```

3. Try to insert sample data into your test index:

- Spreadsheet template > copy (leave columns intact, otherwise you need to change it in /application/controllers/coronacampus/cli.php)
- publish spreadsheet
- change url for spreadsheet, encode url for command line

Run php codeigniter cli on command line (example for Mac OSX & MAMP):

` /Applications/MAMP/bin/php/php7.2.1/bin/php index.php coronacampus/cli loadspreadsheet https%3A%2F%2Fspreadsheets.google.com%2Ffeeds%2Flist%2F1kntJWO9iP6rL6WFqKXNsINoa923LjoDfEz38_NA4-ao%2Fod6%2Fpublic%2Fvalues%3Falt%3Djson`


(For Appbase API actions the logs will be in /application/logs
use tail -f, everything before that will be outputted to command line with custom_log_message)

4. Check data in appbase dashboard (Develop > Browse data)

5. If everything is working, push to production, append 1 as parameter for cli:

```
/Applications/MAMP/bin/php/php7.2.1/bin/php index.php coronacampus/cli loadspreadsheet https%3A%2F%2Fspreadsheets.google.com%2Ffeeds%2Flist%2F1kntJWO9iP6rL6WFqKXNsINoa923LjoDfEz38_NA4-ao%2Fod6%2Fpublic%2Fvalues%3Falt%3Djson 1
```

5. Provide end user access
(e.g. via Github Project reactive-search, fork it or use appbase search preview)


Alternatives for ElasticSearch hosting:
stackhero
