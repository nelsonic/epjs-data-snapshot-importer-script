# epjs-data-snapshot-importer-script

## Why?

> `As a` **SLaM User** <br />
> `I want` **view** my (_patient_) **records** in a simple/convenient way <br />
> `So that` I can **see** & keep track of **my progress**
towards my **health goals**!

For the _original_ issue where we captured the _need_ for this ETL script,<br />
please see: https://github.com/healthlocker/healthlocker/issues/122

## What?

A simple "Extract Transform Load" ("ETL") script that helps us
view the data (snapshot/dump) from "EPJS" ("Electronic Patient Journey System"),
create a database table (_if it does not already exist_)
and import the EPJS data (_snapshot_) for use in the main `Healthlocker` app.

### Requirements

+ Script must be fast to run and require no "_proprietary_" tools.
+ Script must be re-useable. (_not single use_)
+ Re-runable. Given a new data set we should be able
to re-run the script to import new data.


## How?







## Implementation Detail Questions

### JavaScript?

I've decided to write this script in JavaScript (_runs on Node.js_)
Because:
+ We already have node.js for the main app (assets).
+ JS is our "lingua franca" (_everyone on our team can read/write/maintain it_!)

There are other options for writing ETL scrips.
My preferred "_Weapon of Choice_" is <br />
http://www.pentaho.com/product/data-integration
which is the "Sledge Hammer to Crack a Nut" approach. <br />
If you ever need to do a _large_ data migration from various sources,
contact me I will walk you through it. :wink:
