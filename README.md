# Ex.04 Design a Website for Server Side Processing
## Date:

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
nivi.html
<html>
    <head>
        <title>
            Fuelconsumed
        </title>
        <style>
            body
            {
               background-color: rgb(94, 177, 166); 
            }
            .box
            {
               width: 600px;
               height: 300px;
               background-color: rgb(163, 80, 141);
               border:dotted 3px NAVY;
               padding: 10px;
               margin-left: 275px;
               margin-top: 100px;
               position:fixed;
               top: 100px;
               left: 275px; 
            }
        </style>
    </head>
    <body>
        <div class="box">
            <h2 align="center">FUEL EFFICIENCY OF A VEHICLE</h2>
            <h3 align="center">S R NIVEDHITHA (25000724) </h3>
            <h2 align="center">MILEAGE CALCULATION</h2>
            <form method="post" align="center">
                {% csrf_token %}
                <label>Distance:</label>
                <input type="text" name="distance" value="{{ distance }}">
                <br>
                <br>
                <label>Fuel Consumed:</label>
                <input type="text" name="fuel_consumed" value="{{ fuel_consumed }}">
                <br>
                <br>
                <input type="submit" value="calculate">
                <br>
                <label>Mileage:</label>
                <input type="text" name="mileage" value="{{ mileage }}">
            </form>
        </div>
    </body>
</html>

views.py

from django.shortcuts import render
def mileage(request):
    distance = int(request.POST.get('distance', '0'))
    fuel_consumed = int(request.POST.get('fuel_consumed', '1'))
    mileage = distance/fuel_consumed if request.method == 'POST' else 0
    print("distance=",distance)
    print("fuel_consumed=",fuel_consumed)
    print("mileage=",mileage)
    return render(request, 'mathapp/nivi.html', {'distance': distance, 'fuel_consumed': fuel_consumed, 'mileage': mileage})

urls.py


from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [path('',views.mileage,name='vehicle')


## OUTPUT - SERVER SIDE:

![alt text](<Screenshot 2025-12-10 112849.png>)
## OUTPUT - WEBPAGE:

![alt text](<Screenshot 2025-12-10 112557.png>)
## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
