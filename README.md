## Project Title

Yelpish

## Project Description

An app where users can leave reviews and ratings for businesses as well as create business listings.


## GitHub Repo Links

- [Front-end](https://github.com/jeremyhilado/ga-capstone-project-frontend)
- [Back-end](https://github.com/jeremyhilado/ga-capstone-project-backend)

## Project Schedule

| Day | Component |
| --- | :---: |

| 1 | Backend Models & Serializers |
| 2 | Backend Urls |
| 3 | Connect to Frontend and Implemnent GET functionality |
| 4 | Implement Frontend Create Functionality |
| 5 | Implement Frontend Delete & Update Functionality |
| 6 | CSS |
| 7 | CSS |
| 8 | Debugging |

## Wireframes

[Home Page](https://res.cloudinary.com/do6tcpizk/image/upload/v1588958591/GA%20Project%204%20Capstone%20Yelp%20Clone/IMG_3169_uro9yj.jpg)
[Search Page](https://res.cloudinary.com/do6tcpizk/image/upload/v1588958591/GA%20Project%204%20Capstone%20Yelp%20Clone/IMG_3171_fdgean.jpg)
[Create Page](https://res.cloudinary.com/do6tcpizk/image/upload/v1588958591/GA%20Project%204%20Capstone%20Yelp%20Clone/IMG_3173_t7hxap.jpg)
[Update/Delete Page](https://res.cloudinary.com/do6tcpizk/image/upload/v1588958591/GA%20Project%204%20Capstone%20Yelp%20Clone/IMG_3172_lxwwq7.jpg)
[Register User Page](https://res.cloudinary.com/do6tcpizk/image/upload/v1588958591/GA%20Project%204%20Capstone%20Yelp%20Clone/IMG_3170_zutp4q.jpg)

## React Component Architecture

[React Architecture](https://docs.google.com/drawings/d/1aX130-uJ-6ShuQmGKrcZvnOA0qXm3FfQT1NQWQHHr_Q/edit)

## Database Models

from django.db import models
from apps.authentication.models import User


class Business(models.Model):
    name = models.CharField(max_length=255)

    class Meta:
        verbose_name = "Business"
        verbose_name_plural = "Businesses"

    def __str__(self):
        return self.name


class Category(models.Model):
    business = models.ForeignKey(Business, related_name='business_category', on_delete=models.CASCADE)
    alias = models.CharField(max_length=255)
    title = models.CharField(max_length=255)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    owner = models.ForeignKey(User, on_delete=models.CASCADE)

    class Meta:
        verbose_name = "Category"
        verbose_name_plural = "Categories"

    def __str__(self):
        return self.title


class Coordinate(models.Model):
    business = models.ForeignKey(Business, related_name='business_coordinate', on_delete=models.CASCADE)
    latitude = models.FloatField()
    longitude = models.FloatField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    owner = models.ForeignKey(User, on_delete=models.CASCADE)

    def __str__(self):

        return self.latitude + " / " + self.longitude


class Transaction(models.Model):
    business = models.ForeignKey(Business, related_name='business_transaction', on_delete=models.CASCADE)
    []
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    owner = models.ForeignKey(User, on_delete=models.CASCADE)

    def __str__(self):
        return []


class DisplayAddress(models.Model):
    business = models.ForeignKey(Business, related_name='business_displayAddress', on_delete=models.CASCADE)
    []

    def __str__(self):

        return []


class Location(models.Model):
    business = models.ForeignKey(Business, related_name='business_location=', on_delete=models.CASCADE)
    address1 = models.CharField(max_length=255)
    address2 = models.CharField(max_length=255)
    address3 = models.CharField(max_length=255)
    city = models.CharField(max_length=255)
    zip_code = models.IntegerField()
    country = models.CharField(max_length=3)
    state = models.CharField(max_length=2)
    display_address = models.ForeignKey(DisplayAddress, related_name='location_address', on_delete=models.CASCADE)

    def __str__(self):
        return self.display_address


class BusinessAttributes(models.Model):
    business = models.ForeignKey(Business, related_name='business', on_delete=models.CASCADE)
    alias = models.CharField(max_length=255)
    name = models.CharField(max_length=255)
    image_url = models.URLField(max_length=255)
    is_closed = models.BooleanField(default=False)
    url = models.URLField(max_length=255)
    review_count = models.IntegerField()
    categories = models.ForeignKey(Category, related_name='business_category', on_delete=models.CASCADE)
    rating = models.FloatField()
    coordinates = models.ForeignKey(Coordinate, related_name='business_coordinates', on_delete=models.CASCADE)
    transactions = models.ForeignKey(Transaction, related_name='business_transactions', on_delete=models.CASCADE)
    price = models.CharField(max_length=5)
    location = models.ForeignKey(Location,  related_name='business_location', on_delete=models.CASCADE)
    phone = models.CharField(max_length=11)
    distance = models.FloatField()

    def __str__(self):
        return self.name

## MVP / PostMPVP

MVP
 - Be able to add artist info to database, update artist info, create artist info, delete artist info
 
 PostMVP
 - Add artist to favorites list
 - Add other users as friends

## Time / Priority Breakdown

| Component | Priority | Estimated Time | Time Invetsted | Actual Time |
| --- | :---: |  :---: | :---: | :---: |
| Adding Login Form | H | 4 hrs | |
| Creating Backend | H | 4 hrs| | |
| Creating Register User Page | H | 4 hrs | | |
| Creating Search Business Page | H | 4 hr | | |
| Creating Search Results Page | H | 4 hrs | | 
| Creating Update/Delete Page | H | 4 hrs | |
| Creating add Business Page | H | 4 hrs | | |
| Testing | M | 5 hrs | |
| Adding Styling | M | 5 hrs | | |
| Adding About Page | M | 2 hr | |
| Deployment | H | 3hrs | | |
| Implement Favorites list | L | 4 hrs | |
| Total | | 47 hrs | | |

## Additional Libraries

## Code Snippet

## Issues and Resolutions
