# Ex.03 Design a Website for Server Side Processing
## Date:12.11.2026

## AIM:
To create a web page to calculate Churn Rate using server-side scripts.

## FORMULA:
Churn Rate = (CustLost / InitCust) * 100
InitCust --> Initial Customers Count
CustLost --> Customers Lost Count

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create a HTML file to implement form based input and output.

### Step 5:
Create python programs for views and urls to perform server side processing.

### Step 6:
Receive input values from the form using request.POST.get().

### Step 7:
Calculate the Result using the given formula.

### Step 8:
Display the calculated result in the server console.

### Step 9:
Render the result to the HTML template.

### Step 10:
Publish the website in Localhost.

## PROGRAM:
```
<html>
    <head>
        <title>rectangle area calculator</title>
        </head>
        <body bgcolor="lime">
            <h1 align="center">CALCULATOR</h1>
            <h2 align="center">NANDAGOPAL K K</h2>
            <h3 align="center">26017428</h3>
            <form method="POST">
            {%csrf_token %}<br><br>
                

       <B> <label>INITIAL CUSTOMER=</label></B>
        <input type="number" name="initial_cust" value="{{l}}" ><br><br>
        <B><label>PRESENT CUSTOMER=</label></B>
        <input type="number" name="present_cust" value="{{i}}" ><br><br>
        <B><input type="submit" value="Calculate"><br><br></B>
        <B><label>CHURN RATE=</label></B>
        <input type="number" value="{{churnrate}}"><br><br>

            
        </body>

views.py

from django.shortcuts import render

def churn_rate(request):
    l = float(request.POST.get('initial_cust', '0'))
    i = float(request.POST.get('present_cust', '0'))

    churnrate = (l/i)*100 if request.method == 'POST' and i != 0 else 0

    print("InitialCustomer =", l)
    print("PresentCustomer=", i)
    print("Churnrate =", churnrate)

    return render(
        request,
        'myapp/math.html',
        {'l': l, 'i': i, 'churnrate': churnrate}
    )






url.py

from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('', views.churn_rate, name='churn_rate'),
]




```

## OUTPUT - SERVER SIDE:
![alt text](<Screenshot (34).png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot (36).png>)

## RESULT:
The the web page to calculate Churn Rate using server-side scripts is created successfully.
