from unittest.mock import DEFAULT

from django.db import models
from django.utils.regex_helper import Choice
from unicodedata import category, decimal

# Create your models here.
COLLEGE_NAME_CHOICE =[

    ('MIT', 'Massachusetts Institute of Technology'),
    ('STAN', 'Stanford University'),
    ('HARV', 'Harvard University'),
]

COURSEDETALI_CATEGORY_CHOICE = [
    ('tech', 'Technology'),
    ('biz', 'Business'),
    ('art', 'Arts'),
]

class Collegedetail(models.Model):
    name = models.CharField(max_length=60)
    college_name = models.CharField(max_length=60,choices =COLLEGE_NAME_CHOICE,default='mit')
    address = models.CharField(max_length=70)
    phone = models.CharField(max_length=10)
    email = models.EmailField(blank=True,null=True)
    estabilted_year = models.DateField()
    city = models.CharField(max_length=70)
    is_active = models.BooleanField(default=False)
class Feesdetail(models.Model):
    amount = models.DecimalField(max_digits=10,decimal_places=9)
    dection = models.CharField(max_length=60)

def __str__(self):
    return self.name



class Coursedetali(models.Model):
    name = models.CharField(max_length=60,verbose_name="name")
    category = models.CharField(max_length=60, choices=COURSEDETALI_CATEGORY_CHOICE,default='tech')
    duration = models.TextField()
    sets = models.FloatField()
    fees = models.ForeignKey(Feesdetail, on_delete=models.CASCADE)


