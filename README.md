```
   _____       _                   _       
  / ____|     | |                 (_)      
 | (___  _   _| |_ __ _  ___       _  ___  
  \___ \| | | | __/ _` |/ __|     | |/ _ \ 
  ____) | |_| | || (_| | (__   _  | | (_) |
 |_____/ \__, |\__\__,_|\___| (_) |_|\___/ 
          __/ |                            
         |___/                              

                     ./work ./share ./relax 
```

# Sytac Development Challenge #

Congratulations to making it this far! The next step in the hiring process consist in a small coding assignment. 
We would like to know you better, and there is no better way than to see how you code!

We appreciate that you may be doing this assignment next to your day job. Or you might have set a weekend aside to
complete it. Please let our Sytac HR know how much time you need to complete this challenge. You are 
**not** evaluated on time.

> This challenge has been carefully crafted so that it would require an experienced developer somewhere between 4 and 
> 6 hours to complete. If you find yourself spending considerably more time, please reach out to your 
> Sytac HR and ask for guidance.

## Code review/evaluation criteria 🏅

Your submission will be evaluated by Sytac on the following criteria:

+ Requirements coverage completeness
+ Correctness of the implementation
+ Decent test coverage
+ Code cleanliness
+ Efficiency of the solution
+ Careful choice of tools and data formats
+ Use of production-ready approaches

## Delivery format 🚚 ##

Please provide the code as a **Maven** or **Gradle** project.
You are free to choose any language/framework/library that runs on the JVM and fits with the purpose
of the application. Our preference is for **Kotlin** or **Java** languages.

Markdown instructions on how to run the application are always appreciated.

## How to work with GitHub 😼
You are assigned to your own private repository. Please create a feature branch and **do not commit on master**.
When the assignment is completed, please **create a pull request** on the master of this repository,
which will automatically notify your contact person about the completion of your delivery.  

## Software required on your machine 🔧
 - [Docker](https://www.docker.com)
 - [Git](https://git-scm.com)
 - a GitHub account
 - a recent JDK release (11+)
 - your favorite IDE
       
# Your task: the data harvester  🕵️‍♂️ #

Your task, should you choose to accept it, is to create a program that harvest real time usage information
about the users of `video streaming events' server`. The details of the platform and a list of the requirements are available down below.  
In order to fulfill the assignment, you will have to consume three streaming endpoints by running the video streaming events' server on your machine as described [here.](StreamingPlatform.md)

## Mandatory requirements to implement 📜 ##

Your application should collect the data of all three streams for 20 seconds or until the third occurrence
of a user with first name `Sytac` on either of streams, whichever comes first.

The application should output the aggregated view of the data collected, detailing:

+ user id
+ user's name and surname
+ user's age
+ all the events that the user has executed
+ platform where each event has occurred
+ the show titles
+ the first person in the cast for each show, if present
+ the show ids
+ event time in  Amsterdam (CET) timezone and `dd-MM-yyyy HH:mm:ss.SSS` format

and also:

+ the total number of shows released in 2020 or later (for any type of event)
+ for how long the 3 streams were consumed, in milliseconds

The output should be either:

- printed on standard output, or
- written into a file, or
- returned via an HTTP GET request.

You decide the output format and output method, observing that the output data is easily
interpreted by another program **and humans**.

<details>
  <summary>Short on time? Here is a hint 💡</summary>

  ```kotlin
    "PT" -> "UTC"
    "CA" -> "America/Toronto"
    "US" -> "America/Los_Angeles"
    "RU" -> "Europe/Moscow"
    "ID" -> "Asia/Jakarta"
    "CN" -> "Asia/Shanghai"
  ```
</details>

<details>
  <summary>Here is another hint, for good luck 💡💡</summary>
  
   
Unfortunately, the server is bugged: from time to time the data returned is not well-formed.
</details>

## Bonus points 🌟 ##

> The following requirements are optional. Develop these if you are looking to impress us!  

Along with the Mandatory requirements, collect:  

- the total number of `successful streaming events` per user:
  - a successful streaming event is a defined as (sub)sequence of a `stream-started`, followed right after temporally by a `stream-ended` for the same show id and platform. For Example:
    - `[{stream-started, s_01, sytflix, 01_01_2000}, {stream-ended, s_01, sytflix, 01_01_2001}]` => successful event  
    - `[{stream-started, s_01, sytflix, 01_01_2000}, {stream-ended, s_01, sytazon, 01_01_2001}]` => nothing (different platforms)  
    - `[{stream-started, s_01, sytflix, 01_01_2000}, {stream-ended, s_02, sytflix, 01_01_2001}]` => nothing (different shows)
    - `[{stream-started, s_01, sytflix, 01_01_2000}, {show_liked, s_01, sytflix, 01_06_2000}, {stream-ended, s_01, sytflix, 01_01_2001}]` => successful event  
    - `[{stream-ended, s_01, sytflix, 01_01_2000}, {stream-started, s_01, sytflix, 01_01_2001}]` => nothing (no stream end event)

- the percentage of started stream events out of all events occurred on the `Sytflix` platform

# Questions ❓ #

If you have questions regarding the development, reach out to the Sytac recruiter that is taking care of your hiring process. 
They reply the message to the most suitable Sytac technical officer that will answer your queries in a timely manner.
