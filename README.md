<h1>About Project</h1>

This python project helps to notify user for their favorite movies when tickets are availabel by sending SMS to their mobile.

</br>
<b>Note</b>
1. General SMS service provided by Fast2sms is allowed during 9 AM to 9 PM, but for all time service you can get approval of a SMS template at Bulk SMS->Quick Trans(after registering at https://www.fast2sms.com/), after this you can send this template any time otherwise your normal sms will be scheduled at 9 AM next day.
</br>
<h2>Steps to run the code</h2>

<strong>This code has a config file in config folder. All config details are stored in data.json file.</br>
To run the program this data config needs to be set. Starting steps states how to get all details to fill this json file.</br></strong>

<h3>Step 1(Getting Free SMS Service)</h3> 
1. Go to https://www.fast2sms.com/ and register to get free sms service(Initial credit are free to all user).</br>
2. Then go to Dev API and copy authorization key. And in data.json set fast2smsDetails['metaData']['authorization']

<h3>Step 2(Selecting Mobile Number on which you want to send SMS)</h3>
1. Mobile numbers is set at fast2smsDetails['data']['numbers'](comma separated mobile numbers)</br>
2. Set message at fast2smsDetails['data']['message']

<h3>Step 3(Getting Movie link which we want to monitor)</h3>
1. Go to book my show and select a movie for which you want notify yourself when movie ticket is availabel and then copy the link.</br>
<b>Note</b>
1. Select movie based on a city in which you are looking for ticket. Like link below is searching tickets in Kolkata,
e.g. https://in.bookmyshow.com/kolkata/movies/birds-of-prey/ET00112343 </br>
2. Then set fast2smsDetails['data']['movieLink'] to be that link

<h3>Step 4(Selecting services for notification)</h3>
1. In data.json set values of notificationDetails['sms'] = 1 to send SMS to numbers, and notificationDetails['sound'] to make beep sound when link is availabel to book tickets, you can set timing of notification sound in data.json at soundDetails['duration'].
</br>
</br>

Our data.json format
```json
{
  "fast2smsDetails":{
    //can tune with parameters, go through fast2sms details page
    "metaData":{
      //your key
      "authorization":"YOUR_KEY",
      "url":"https://www.fast2sms.com/dev/bulk",
      "sender_id":"FSTSMS",
      "language":"english",
      "route":"p"
    },
    "data":{
      "message":"Now link is available, so you can process as required.",
      //mobile numbers separated via comma
      "numbers":"1111111111,2222222222,3333333333" 
    }
  },
  "showDetails":{
    "metaData":{
      "sleepTime":19 //sleep time for every failed request
    },
    "data":{
      //movie link selecting city or place where you want to book ticket
      "movieLink":"https://in.bookmyshow.com/kolkata/movies/dwitiyo-purush/ET00109271"
    }
  },
  "notificationDetails":{
    //set value to 1 if want to use that service
    "sms":1,
    "sound":0
  },
  "soundDetails":{
    "frequency":6000,
    //duration of beep beep sound
    "duration":5000
  }
}
```
