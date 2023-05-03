import datetime as dt
import pandas as pd
import smtplib
from random import randint

MY_EMAIL = "arshdauwa4@gmail.com"
PASSWORD = ""


def send_email(name, email):
    # Get random email letter from template
    random_letter_number = randint(1, 3)  # generates random number among 1, 2 and 3
    print(random_letter_number)
    random_letter = f"letter_templates/letter_{random_letter_number}.txt"
    with open(random_letter) as file:
        content = file.read()
        content = content.replace("[NAME]", name)
    with smtplib.SMTP("smtp.gmail.com") as connection:
        connection.starttls()
        connection.login(user=MY_EMAIL, password=PASSWORD)
        connection.sendmail(from_addr=MY_EMAIL,to_addrs=email,msg=f"Subject: Happy Birthday!!\n\n{content}")


now = dt.datetime.now()
month = now.month
day = now.day

birthdays = pd.read_csv("birthdays.csv")
for index, row in birthdays.iterrows():
    if day == row['day'] and month == row['month']:
        send_email(name=row['name'], email=row['email'])
