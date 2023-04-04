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

# The video streaming events server 📺 #

The `video streaming events server` exposes near real-time information regarding tv shows and movies streamed by users
on 3 fictitious streaming platform: `Sytflix`, `Sytazon` and `Sysney`.  
Each of the endpoint exposes infinite stream representing either the start of a streaming (`stream-started`) ,
the end of a streaming (`stream-ended`), liking a show (`show-liked`) or a problem during the streaming of a show
(`stream-interrupted`).

An example message from the stream is shown below:

```
id:664c318c-6f36-424f-adb9-56f7861aba27
event:show-liked
data:{
  "show": {
    "show_id": "s8105",
    "cast": "Marlon Brando, Bruce Willis",
    "country": "Netherlands, Belgium",
    "date_added": "April 7, 2017",
    "description": "A quarter-century later, this documentary relocates the male dancers who backed Madonna on her 1990 Blond Ambition tour, as seen in \"Truth or Dare.",
    "director": "Ester Gould, Reijer Zwaan",
    "duration": "85 min",
    "listed_in": "Documentaries, International Movies, LGBTQ Movies",
    "rating": "TV-MA",
    "release_year": 2016,
    "title": "Strike a Pose",
    "type": "Movie",
    "platform": "Sytflix"
  },
  "event_date": "27-02-2023 03:20:17.111",
  "user": {
    "id": 116,
    "date_of_birth": "31/10/1970",
    "email": "gbeeton37@wikimedia.org",
    "first_name": "Guenna",
    "gender": "Female",
    "ip_address": "96.34.189.33",
    "country": "TH",
    "last_name": "Beeton"
  }
}

```

The `event_date` specifies the user's local time. `Amsterdam (CET)` is the default time zone.
For the users residing in the countries specified in the table below, the `event_date` is provided
in the corresponding time zone.

| User's Residence Country | Country Code | `event_date` Time Zone       |
|--------------------------|--------------|------------------------------|
| Portugal                 | PT           | Europe/Lisbon (UTC)          |
| Canada                   | CA           | America/Toronto (UTC -5)     |
| United States            | US           | America/Los_Angeles (UTC -8) |
| Russia                   | RU           | Europe/Moscow (UTC +3)       |
| Indonesia                | ID           | Asia/Jakarta (UTC +7)        |
| China                    | CN           | Asia/Shanghai (UTC +8)       |

### How to run the video streaming events server locally ###

You will need Docker installed on your machine. And then from the terminal type:

For Intel/AMD x64 based CPUs:  
```shell
docker run -p 8080:8080 sytacdocker/video-stream-server:latest
```

For Arm based CPUs (Apple with M1/M2 chip):  
```shell
docker run -p 8080:8080 sytacdocker/video-stream-server-arm:latest
```

Once the server is running, you will have several endpoints available on your machine:
- [Sytflix](http://localhost:8080/sytflix) (`http://localhost:8080/sytflix`);
- [Sytazon](http://localhost:8080/sytazon) (`http://localhost:8080/sytazon`);
- [Sysney](http://localhost:8080/sysney) (`http://localhost:8080/sysney`).

All the endpoints are protected by username and password (basic auth):
```
username = sytac
password = 4p9g-Dv7T-u8fe-iz6y-SRW2
```