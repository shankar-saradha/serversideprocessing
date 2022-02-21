# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Create a django project inside the pulled GitHub Repo.



### Step 2:
Insdie the project create a app called mathapp using command "sudo python3 manage.py startapp mathapp".


### Step 3:
Create a template folder inside mathapp and inside than create another folder called mathapp and inside that create a new file "area.html"


### Step 4:
Add the html conents in the area.html.


### Step 5:
Do the mathemical calculation in views.py and link the html tags.


### Step 6:
Link the html file through views.py in urls.py.

Publish the website in the given URL.

## PROGRAM :
HTML:
~~~html 
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Cuboid</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <link rel='stylesheet' href="./style.css">
</head>
<body style="text-align: center;background-color: whitesmoke;color:rgb(224, 12, 12);">
    <!--Hi there-->
    <h1>Volume of Cuboid</h1>
    <div style="display: block; background-color: #970d0d;text-align: center;border-radius: 20px;width: 800px; height: 310px; margin-left: auto; margin-right: auto;">
        <form method="POST" style="padding-top: 25px;color: whitesmoke;">
            {% csrf_token %}
            Base = <input type="text" name="base" value="{{b}}" style="text-align: center;border-radius: 20px;text-align: center;box-shadow: 1.5px 7px #970d0d;background-color: #e97b7b;" > m <br/>
            <br/>
            Height = <input type="text" name="height" value="{{h}}" style="text-align: center;border-radius: 20px;text-align: center;box-shadow: 1.5px 7px #970d0d;background-color: #e97b7b;"> m <br/>
            <br/>
            Length = <input type="text" name="length" value="{{l}}" style="text-align: center;border-radius: 20px;text-align: center;box-shadow: 1.5px 7px #970d0d;background-color: #e97b7b;"> m <br/>
            <br/>
            <input type="submit" value="Calculate" style="text-align: center; width: 100px;border-radius: 20px;text-align: center;box-shadow: 1.5px 7px #970d0d;background-color: #e97b7b;" ><br/>
            <br/>
            Volume = <input type="text" name="area" value="{{area}}"style="text-align: center;border-radius: 20px;text-align: center;box-shadow: 1.5px 7px #970d0d;background-color:#e97b7b;"> m<sup>3 </sup><br/>
        </form>
        <u> <h2 style="color: wheat;">By Shankar  P</h2></u>
    </div>
</body>
</html>
~~~
view.py
~~~ python 
from django.shortcuts import render
def areacalculation(request):
    context = {}
    context["area"] = "0"
    context["b"] = "0"
    context["h"] = "0"
    context["l"] = "0"
    if request.method == "POST":
        b = request.POST.get("base","0")
        h = request.POST.get("height","0")
        l = request.POST.get("length","0")
        volume = int(b) * int(h) * int(l)
        context["area"] = volume
        context["b"] = b
        context["h"] = h
        context["l"] = l
    return render(request,"app/area.html",context)
  ~~~
 url.py
~~~python 
from django.contrib import admin
from django.urls import path
from app import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path("areaofrectangle/",views.areacalculation,name="areaofrectangle"),
    #The below line is to display the html page on our site without /staic/areaofreactangle.
    path("",views.areacalculation,name="areaofrectangleroot")
]
~~~
## OUTPUT:
![webside server ](https://user-images.githubusercontent.com/93978702/154943167-4fcf3574-e79c-4590-9548-5a0965962bb9.png)



## Result:

Thus a website is designed to perform mathematical calculations in server side 
