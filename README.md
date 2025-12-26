# Ex.05 Design a Website for Server Side Processing
## Date:01.10.2025

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
```
math.html
html
<!DOCTYPE html>
<html>
<head>
    <title>BMI Calculator</title>
</head>
<body>
    <form method="POST">
  {% csrf_token %}
  <label>Height (cm):</label>
  <input type="text" name="height"><br>
  <label>Weight (kg):</label>

  <input type="text" name="weight"><br>

  <button type="submit">Calculate</button>
</form>

{% if BMI %}
  <h3>Your BMI is: {{ BMI }}</h3>
{% endif %}
</body>
</html>

views.py


from django.shortcuts import render

def calculate_bmi(request):
    bmi = None

    if request.method == "POST":
        try:
            height_cm = float(request.POST.get("height"))
            weight_kg = float(request.POST.get("weight"))
            height_m = height_cm / 100  # convert cm to meters
            
            bmi = weight_kg / (height_m * height_m)

            print(f"Calculated BMI: {bmi:.2f}")  # Output to console

        except (TypeError, ValueError, ZeroDivisionError):
            bmi = None

    return render(request, "bmiapp/bmi.html", {"BMI": bmi})

    urls.py

    from django.contrib import admin
from django.urls import path
from bmiappimport views
urlspatterns =[
    path('admin/',admin.site.urls),
    path('calculatedbmi/',views.calculate_bmi,name="calculatedbmi"),
    path('',views.calculate_bmi,name="calculatedbmiroot")
]
```


## SERVER SIDE PROCESSING:
<img width="1920" height="1080" alt="Screenshot (36)" src="https://github.com/user-attachments/assets/d8280079-0d5f-4458-a909-f7ffd60c9f3f" />


## HOMEPAGE:
<img width="1920" height="1080" alt="Screenshot (35)" src="https://github.com/user-attachments/assets/1398eef9-77d1-40b1-8c01-d40d0c0dec16" />

## RESULT:
The program for performing server side processing is completed successfully.
