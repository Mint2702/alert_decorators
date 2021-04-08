# Gmail Alert System

## About

A system that alerts you if you python script had an error while processing. Alerting you is done by writing you an gmail with an error in it.

It can be helpful when you have a script that runs on your server continuously as a deamon (like a web server) or it automaticaly runs over some period of time, and you want to know if it failed to finish as quicly as possible.

## Features

The system has two decorators - *alert_async* and *alert_sync*. The *alert_async* decorator is used for coroutines and the *alert_sync* decorator is used for synchronious function.

## Usage

For integration with your python code, you need to:
1. Download all needed libraries from the requirements.txt file 
```bash 
pip install -r requirements.txt
```
2. Place the gmail.py file in your /core folder or anywhere else you want it to be
3. Create .env file one folder up from gmail.py file (or just use the .env file that you have already been using). You can also change the route to the .env file from gmail.py if you need to.
4. In the .env file add two lines, filling gmail adress and password:
```env
GMAIL_PASSWORD = example_password
GMAIL = example_gmail@gmail.com
```
5. From gmail.py module import one of two decorators into your main module, where the starting function is (it is probably the main.py file):
```python3
from core.gmail import alert_async
```
or 
```python3
from core.gmail import alert_sync
```
6. Then use *logger.catch* and *alert_async*/ *alert_sync* decorators for your main() function:
```python3
@logger.catch
@alert_async
async def main():
    .
    .
    .
```
or:
```python3
@logger.catch
@alert_sync
def main():
    .
    .
    .
```

## Additional information about logging with gmail

You might need to change some setting in your Google Account to use this system. 
You need to:
1. Search google for:           "Turn on Less secure app access "
2. Click the first:                   "support.google" link
3. Click the dropdown:       "If Less secure app access is off for your account"
4. Click:                                  "Turn it back on"
5. Toggle:                               "Allow less secure apps: ON" 

If you have a 2 factor authentication in Google Account turned on, then you might need to set new password for a sertain machine to use gmail on it. 

## Examples

You can check how I use this system here:
- [Delete_old_records](https://github.com/Mint2702/delete_old_records_erudite_drive)
- [Synchronazation_of_Erudite_Ruz_and_GoogleCalendar](https://github.com/Mint2702/gcalendar_ruz)

