# Osint Tool
This is a combined tool for Osint. It can be used in both GUI and CLI mode.

![1](https://user-images.githubusercontent.com/46415431/181070640-648f5e11-3720-4cbb-a1d0-94b4036c6e4b.jpg)
![2](https://user-images.githubusercontent.com/46415431/181070656-96b4633c-2359-42b1-afc7-3e00d56c488c.jpg)

## Features
### 1. Username Lookup
- It checks given username & find out sevral websites where the same username exist.

![3](https://user-images.githubusercontent.com/46415431/181071771-a35695ed-b31b-4968-b3ff-dacc2bf0a095.png)

### 2. Email Lookup
1. It find out other websites where the given email is registerd or used.
2. Checks for data breaches where the given is present and give detailed information about data breach.
3. If the given email is gmail then it gives information about that google account. Including name, photo and google map reviews.


![4](https://user-images.githubusercontent.com/46415431/181071815-d0b8b57b-256f-4697-ac16-e7e6bdc09ffa.png)
![5](https://user-images.githubusercontent.com/46415431/181071818-1fbe121b-4cc7-4149-9bc3-fc139ba4ca70.png)
![6](https://user-images.githubusercontent.com/46415431/181071821-20d8a818-f4c0-41f3-a885-60070a881e73.png)


### 3. Phone Lookup
- It gives you owner name, carrier info and city or state name of given phone number. (As of now it only works for indian phone numbers.)

![7](https://user-images.githubusercontent.com/46415431/181071864-5987e727-7fc9-406f-b8f5-592b5ebc57c5.png)

### 4. Website Lookup
1. First it gives basic info realted to given website. Like ip, serever address & ISP info.
2. Then it gets whois information of given domain.
3. It gets subdomains of given domain.
4. It scan for reverse ip for getting other domains on the same server.

![151505338-1c9d8169-ab55-4998-b143-b58a8febba7f](https://user-images.githubusercontent.com/46415431/181071904-4755098a-eae4-4840-9883-c6a5b75c65ea.gif)

## Installation
1. Python3 must be installed on your system.
2. Git clone this repo or download the zip and extract it in a folder. `git clone https://github.com/R4JVE3R/OsintTool.git`
3. Install the requirements. For that go to `OsintTool` folder and run this command. `pip install -r requirements.txt`
## Setup
- Goto `OsintTool` folder, open .env file and edit environment variable's values accordingly.
1. `HIBP_KEY` is a Have I Been Pwned API Key. It is used to fetch data breaches of the email. You can get this api key from [here](https://haveibeenpwned.com/API/Key). It will cost 3.5$ for a month. If you dont have this API key, leave `HIBP_KEY` empty and email breach module will be skipped.
2. `G_COOKIE`, `HANGOUTS_Authorization`, `HANGOUTS_KEY`, `GDRIVE_Authorization` and `GDRIVE_KEY` are required to get google info of the given email. To get these values, follow below steps.
    - `G_COOKIE` is combined of 3 cookies values `__Secure-1PSID`, `__Secure-3PSID` and `__Secure-3PAPISID`.
       - Open mail.google.com or myaccount.google.com, open inspect element and go to storage tab.![cookie](https://user-images.githubusercontent.com/46415431/181072009-9cebfd42-0d84-4b6c-9b15-f82cea1211ea.png)
 Copy these 3 cookie's values, combine them like `__Secure-1PSID=whatever;__Secure-3PSID=whatever;__Secure-3PAPISID=whatever;` and set this as `G_COOKIE`'s value.
    - For `HANGOUTS_Authorization` and `HANGOUTS_KEY`, open hangouts.google.com, open network tab of the browser and search for `people-pa.clients6.google.com` domain. There will be one post request, key parameter is our `HANGOUTS_KEY`. So copy that value and paste it as `HANGOUTS_KEY`'s value. ![key](https://user-images.githubusercontent.com/46415431/181072158-b6913cfc-7090-4a27-983f-74bdc1a48c6c.png) Scroll down to request headers and you will find Authorization header. Copy it's value and paste it as `HANGOUTS_Authorization`'s value.  ![auth](https://user-images.githubusercontent.com/46415431/181072242-57a42d54-492f-4c0e-9850-6e1a7074e00f.png)
    - For `GDRIVE_Authorization` and `GDRIVE_KEY`, open drive.google.com, open network tab of the browser and search for `people-pa.clients6.google.com` domain. There will be one post request, key parameter is our `GDRIVE_KEY`. So copy that value and paste it as `GDRIVE_KEY`'s value. Scroll down to request headers and you will find Authorization header. Copy it's value and paste it as `GDRIVE_Authorization`'s value.

4. `TRUECALLER_AUTH` is an Authorization Bearer of truecaller. It is used to retrive the data of given phone number from truecaller. To get this, you need to have trucaller app installed on your device, login to the app, intercept any request and you will find `Authorization` header in the request. Copy the Authorizarion Bearer and paste it here.
5. `WHOIS_KEY` is an IP2WHOIS API key. It is used to get whois data of the given domain. It is free, you can get this API key from [here](https://www.ip2whois.com/developers-api).
6. `SECURITYTRAILS_KEY` is a SecurityTrails API Key. It is used to get subdomains of the given domain. It is also free, you can get this API Key from [here](https://securitytrails.com/corp/api).
## Usage
1. To use it in CLI mode. You can run `python OsintTool.py -h` command to see help.
   - There are 4 flags available for different 4 modules. Examples are given below.
     1. Username lookup: `python OsintTool.py -u example`
     2. Email lookup: `python OsintTool.py -e test@test.com` 
     3. Phone lookup: `python OsintTool.py -p 1234567890`
     4. Website lookup: `python OsintTool.py -w google.com`
 2. To use it in GUI mode.
    - Run server.py `python server.py`
    - Navigate to http://127.0.0.1:5000 to access GUI mode.
## Credits
1. [Sherlock](https://github.com/sherlock-project/sherlock) - For username lookup, I have used sherlock and modified it according to my requirements.
2. [Holehe](https://github.com/megadose/holehe) - In email lookup, to check whether the given email is used to different websites, I have used holehe and modified it according to my requirements.
