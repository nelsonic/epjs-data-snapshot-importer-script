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

This is a **_complete "step-by-step"_ log** of my process/progress.
If it feels like there is "_too much detail_", consider "_skimming_" it. <br />
Also, "_too much detail_" is ***alwyas*** better than _too little_ when it comes
to technical projects.

### Step 1: Get "Raw" Data

Locate the `DB_DUMP.zip` archive:

![epjs-data-file-view](https://cloud.githubusercontent.com/assets/194400/23403076/60d7e6ae-fda6-11e6-9e7e-4db0ebc0aee3.png)

### Step 2: Extract (Unzip) the Data from the `DB_DUMP.zip` Archive

![carenotes-unzipped](https://cloud.githubusercontent.com/assets/194400/23403491/45f74ff8-fda8-11e6-8af5-a95b0f9936e6.png)

**423MB** is quite a _lot_ of data ...
"ETL" (_to extract just the parts we need_) is ***essential***.

Sadly the `.BAK` file is _useless_ to us. <br />
Attempting to open it in your Text Editor is _pointless_:<br />
![image](https://cloud.githubusercontent.com/assets/194400/23403333/92c0ae70-fda7-11e6-9a84-88177b1436c6.png)


### Step 3: Ask for Help!

Faced with a "_Blob_" of Data and No way to "Read" it ... ask for help!

![ask for help from product owner](https://cloud.githubusercontent.com/assets/194400/23403860/00d71636-fdaa-11e6-9b57-da99a0528a46.png)

**Note**: occasionally, when I need to get "High Priority" done and
I don't _know_ if the person I need help from <br />
checks their GitHub notifications,
I will "_follow up_" by email: <br />
![follow up email](https://cloud.githubusercontent.com/assets/194400/23404133/459a8d06-fdab-11e6-833a-7aaa47943962.png)
<br />Refer to the issue on **GitHub** so
the means of communication is still **GitHub**
which is where we have our "***Single Source of Truth***". <br />
`email` is simply to "_notify_" the **Product Owner**
(_and "CC" the "Scrum Master" so they are also aware_)
that assistance is requested/required.

Thankfully the project "***Product Owner***" ([_Mollie_]()) is "_on the ball_" and forwarded
our request to Garry (Moriarty [`#RealName`](https://www.linkedin.com/search/results/index/?keywords=Garry%20Moriarty) :wink:): <br />
![epjs-request-email](https://cloud.githubusercontent.com/assets/194400/23404944/8aa24318-fdaf-11e6-9f71-d8dbca958e20.png)


### Step 4: Attempt to Make Progress `while` Waiting for a Reply!

So we have a `.BAK` file and no _obvious_ way to "_read_" it.
If this is the
[_highest priority_](https://github.com/healthlocker/healthlocker/labels/priority-1)
issue/task/activity on your list for the day, which in my case it is:<br />

![high-priority-tasks](https://cloud.githubusercontent.com/assets/194400/23405145/d779f234-fdb0-11e6-87c7-8b0bc5f9b4b9.png)

***Don't Wait*** for a reply from the Product Owner
or Scrum Master or "_External Dependency_"
**be _Proactive_** and start ***searching*** for a _solution_!

#### Step 4.1: Describe What you Are _Trying_ To do

This is my "_goal_":

> open/import `.BAK` database backup file in PostgreSQL

So I take the keywords and start searching:

![google-search-bak-file](https://cloud.githubusercontent.com/assets/194400/23404433/e677bbda-fdac-11e6-9619-94f0945980f0.png)

I then click on _all_ the links in the Search Results page and start
reading to see if someone `else` has managed to solve the challenge `before`!

http://dba.stackexchange.com/questions/20078/can-i-restore-a-sql-server-bak-files-without-sql-server

The ["most up-voted answer"](http://dba.stackexchange.com/a/20082/89486)
instructs to use a Virtual Machine to download a trial of Microsoft SQL Server
... so not a "_quick_" solution...



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
