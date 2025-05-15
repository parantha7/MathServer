# Ex.05 Design a Website for Server Side Processing
# Register Number: 212224040232
## Date:15/05/2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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

## PROGRAM :
math.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        body {
            background-color: #b54141;
            font-family: 'Poppins', sans-serif;
            padding: 40px;
            margin: 0;
        }
        .Calculate {
            width: 30%;
            padding: 25px;
            margin: auto;
            background-color: #cb9d9d;
            text-align: center;
            border-radius: 15px;
        }
        label {
            font-size: 20px;
            color: #ffffff;
            display: block;
            margin-top: 10px;
            text-align: left;
        }
        p {
            font-size: 20px;
            font-weight: bold;
            color: #ffffff;
            margin-top: 20px;
        }
        h1 {
            text-align: center;
            color: #ffffff; 
            margin-bottom: 30px;
        }
        input, button {
            padding: 12px;
            margin: 10px 0;
            width: 90%;
            border: 1px solid #1d0909;
            border-radius: 8px;
            font-size: 16px;
        }
        input {
            background-color: #953838;
            color: #ffffff; 
        }
        button {
            background-color: #ec0d0d; 
            color: #ffffff; 
            font-weight: bold;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #757575;
        }
    </style>
    <title>Document</title>
</head>
<body>
    <h1>Calculating Power of a Lamp</h1>
    <div class="Calculate">
        <form action="{% url 'home' %}" method="post">
            {% csrf_token %}
            <label>Intensity:</label><br>
            <input type="text" name="intensity-input"><br>

            <label>Resistance:</label><br>
            <input type="text" name="resistance-input"><br>

            <button type="submit">Calculate</button>

            <p>The power of the lamp is: {{ output }}</p>
        </form>
    </div>
</body>
</html>
```
views.py
```
from django.shortcuts import render

def power(request):
    if request.method == 'POST':
        intensity_value = int(request.POST.get('intensity-input'))
        resistance_value = int(request.POST.get('resistance-input'))
        power = (intensity_value ** 2) * resistance_value
        return render(request, 'mathapp/math.html', {'output': power})
    return render(request, 'mathapp/math.html')
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('', views.power, name='home')
]
```


## SERVER SIDE PROCESSING:

![alt text](<Screenshot 2025-05-15 190334.png>)

## HOMEPAGE:

![alt text](<Screenshot (30).png>)

## RESULT:
The program for performing server side processing is completed successfully.
