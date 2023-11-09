# django-osnove
********************************************
$ django-admin startproject <ime-sajta> - kreacija projekta
python <ime-funkcije(manage)>.py runserver - podizanje servera
$ python <ime-funkcije(manage)>.py startapp polls - ptavljenje polls direktorijuma
$ python manage.py migrate
$ python manage.py makemigrations polls
$ python manage.py createsuperuser

********************************************
views

from django.http import HttpResponse
from django.shortcuts import render
def <ime-funkcije>(request):
	return render(request,"<ime-fajla>.html")

********************************************
settings

INSTALLED_APPS = [
    'polls.apps.PollsConfig',
    ...
    ]

TIME_ZONE = 'Europe/Belgrade'

********************************************
urls(polls)

from django.urls import path
from . import views

urlpatterns = [
    path("", views.<ime-funkcije>, name="<ime-funkcije>"),
]

********************************************
urls(<ime-projekta>)

from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("", include("polls.urls")),
    path("admin/", admin.site.urls),
]

********************************************
models

from django.db import models

class <ime-entiteta>(models.Model):
    <ime-drugog-entiteta> = models.ForeignKey(url 'downloadexcel', on_delete=models.CASCADE) - funkcija koristi primarni kljuc drugog entiteta
    <ime-atributa-1> = models.CharField(max_length=200) - deklarisanje atributa 
    <ime-atributa-2> = models.IntegerField(default=0) - deklarisanje atributa
    <ime-atributa-3> = models.<(Auto,BigAuto,BigInteger,Binary,Boolean,Char,Date,Decimal,Duration,Email,File,FilePath,Float,Image,Integer,JSON,PositiveBigInteger,PositiveInteger,Slug,SmallAuto,SmallInteger,Text,Time,URL,UUID>Field(default=0) - deklarisanje atributa

https://docs.djangoproject.com/en/4.2/ref/models/fields/#django.db.models.AutoField - tipovi podaataka link

********************************************
admin

from django.contrib import admin

from .models import <ime-entiteta>

admin.site.register(ime-entiteta)
*********************************************
{% load static %}
<link rel="stylesheet" href="{% static '<ime cssa>.css' %}">
