# Ex.05 Design a Website for Server Side Processing
# Date:16.09.2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
 math.py
 {%load static%}
 <!DOCTYPE html>
 <html lang="en">
 <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .calculator {
            background: black;
            color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }
        input {
            width: 80%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        output {
            display: block;
            margin-top: 15px;
            font-size: 1.2em;
        }
        button {
            background-color: #007BFF;
            color: #fff;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
 </head>
 <body>
    <div class="calculator">
        <h2>Power Calculator</h2>
        <form method="POST">
            {% csrf_token %}
        
            <label name='intensity' for="INTENSITY">INTENSITY</label>
                <input type="text" name='intensity' placeholder="Enter 
intensity" id="intensity" value="{{i}}"> <br>
        
             
           <label name="resistance" for="RESISTANCE" 
id="res">RESISTANCE</label>
                <input type="text " name="resistance" placeholder="Enter 
resistance" id="resistance" value="{{r}}"> <br>
         
            <button type="submit">Calculate Power</button> <br>
            <label name="power" for="POWER">POWER</label>
            <input type="text" placeholder="Answer" id="power" name="power" 
value="{{power}}" >
            
        </form>
        
    </div>
 </body>
</html>
 urls.py
 from django.contrib import admin 
from django.urls import path 
from maths import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
 ]
 views.py
 from django.shortcuts import render
 def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'math.html',context)
```
# SERVER SIDE PROCESSING:
![Screenshot 2024-12-19 211610](https://github.com/user-attachments/assets/f2b345c5-0f5f-429e-b5f2-85bee74ac039)

# HOMEPAGE:
![image](https://github.com/user-attachments/assets/09266af9-9a2a-4d62-ac23-71206e1dff6e)

# RESULT:
The program for performing server side processing is completed successfully.
