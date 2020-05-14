## Project Title

The Rundown

## Project Description

An app where users can leave reviews and ratings for businesses as well as create business listings.


## GitHub Repo Links

- [Front-end](https://github.com/jeremyhilado/yelp-clone-frontend)
- [Back-end](https://github.com/jeremyhilado/yelp-clone-backend)

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
```
class Business(models.Model):
    name = models.CharField(max_length=255)
    image_url = models.URLField(max_length=255, blank=True)
    category = models.CharField(max_length=255)
    location_city = models.CharField(max_length=255)
    location_state = models.CharField(max_length=2)
    price = models.CharField(max_length=5)
    phone = models.CharField(max_length=10)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    owner = models.ForeignKey(User, on_delete=models.CASCADE)
    is_public = models.BooleanField(default=True)

    class Meta:
        verbose_name = "Business"
        verbose_name_plural = "Businesses"

    def __str__(self):
        return self.name


class Review(models.Model):
    business = models.ForeignKey(Business, related_name='business_review', on_delete=models.CASCADE)
    rating = models.FloatField()
    review = models.TextField(blank=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    owner = models.ForeignKey(User, on_delete=models.CASCADE)
    is_public = models.BooleanField(default=True)

    def __str__(self):
        return self.business.name + " - " + self.review
```

## MVP / PostMPVP

MVP
 - Be able to add business info to database, update business info, create business listing, delete business listings.
 - Be able to create, update, and delete business reviews.
 
 PostMVP
 - Add businesses to favorites list.
 - Add other users as friends.

## Time / Priority Breakdown

| Component | Priority | Estimated Time | Time Invetsted | Actual Time |
| --- | :---: |  :---: | :---: | :---: |
| Adding Login Form | H | 4 hrs | 1 hr | 1 hr |
| Creating Backend | H | 4 hrs| 8 hrs | 8 hrs |
| Creating Register User Page | H | 4 hrs | 1 hr | 1 hr |
| Creating Search Business Page | H | 4 hr | | |
| Creating Search Results Page | H | 4 hrs | | 
| Creating Update/Delete Review Page | H | 4 hrs | 5 hrs | 5 hrs |
| Creating add Business Page | H | 4 hrs | | |
| Testing | M | 5 hrs | 5 hrs | 5 hrs |
| Adding Styling | M | 5 hrs | | |
| Adding About Page | M | 2 hr | |
| Deployment | H | 3hrs | 5 hrs | 5 hrs |
| Implement Favorites list | L | 4 hrs | |
| Total | | 47 hrs | | |

## Additional Libraries
axios
bootstrap
react-bootstrap
react-router-dom


## Code Snippet
```
<textarea className="form-control" id="exampleFormControlTextarea1" rows="3" name="review" value={rundownContext.reviewInfo.review} onChange={rundownContext.handleReviewChange}></textarea>
                    </div>
                    <button type="submit" className="btn btn-info" name="business" value={business[0].id} onClick={rundownContext.handleReviewChange}>Post Review</button>
```



## Issues and Resolutions
Spent too much time trying to replicate yelp's API exactly in Python and trying to match all the nesting and depths of data. Things got so convoluted I had to undo it all and settle for two simple models that were easy to work with.

Could not figure out how to deploy backend with DEBUG=FALSE.

Spent too much trying to figure out why I couldn't delete things when it ended up I was just missing a '/' at the end of my URL.

Was researching how to get the value of radio buttons and couldn't find any satisfying answers but I was able to figure it out through trial and error on based on what I knew about getting the value of other types of inputs.







