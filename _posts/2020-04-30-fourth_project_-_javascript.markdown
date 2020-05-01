---
layout: post
title:      "Fourth Project - Javascript"
date:       2020-05-01 02:14:25 +0000
permalink:  fourth_project_-_javascript
---


For my fourth project I decided to create something around coffee. I recently got into different brewing methods and making it taste better, so one thing I want to do is try fresh coffee beans from local roasters. This app keeps track of coffee roasters, and their coffees that you've tried. You can create new roasters and coffees that belong to that roaster. Although I feel that this topic has been done before, I definitely want to take this app further in the future.

The main goal of this project was to learn Javascript, which I had a lot of trouble with understanding. The syntax is definitely what confused me the most, among other things. A lot of concepts are similar to Ruby, and this helped in understanding a lot better. A new concept to grab was the fetch request, which I had to do additonal resarch on.

### Fetch

From what I learned, when we call the `fetch(theUrl, data)` method the browser sends a certain request to the url which is received by the backend server and API. These requests are HTTP methods such as GET or POST requests, like we did in the Sinatra and Rails projects except in Javascript. Requests other than GET will need to be specified in the second `data` argument. The API will receive that request and send back code (based on type and other properties) as a response.

This process is done asynchronously, which allows us to create a single page application and perform actions without a manual refresh of the page. When fetch is called it returns a promise, sends a request to the API, and if the browser successfully receives the response from the URL, the promise gets resolved and goes through callback methods (`.then`). Otherwise, the promise will be rejected and an error will be returned.

If the promise is successfully resolved, the `.then` "success" callbacks will then run with the data from the response passed in as the params. Otherwise there will be an error, and this is where the `.catch` failure callbacks run and are important to show in the browser.

```
fetch("http://localhost:3000/api/v1/roasters")
  .then(response => response.json())
  .then(json => console.log(json))
  .catch(error => console.log(error));
```

In the first successful callback function above, the data is received in JSON format (which is easier to deal with) and the second success callback will print the response to the console in the browser. 

```
    fetch("http://localhost:3000/api/v1/coffees", {
        method: "POST",
        headers: {
            "Content-Type": "application/json",
            "Accept": "application/json"
        },
        body: JSON.stringify(coffee)
    })
        .then(response => {
            return response.json()
        })
        .then(coffee => {
            if (coffee.errors) {
                throw new Error(coffee.errors.join(", "))
            } else {
                loadRoasters()
            }
        })
        .catch(alert)
```

To create a coffee, here is my fetch method for the POST request for coffees. I made a fetch to the Url, and the specified a POST method with headers as `application/json` and converts the body of the JSON coffee object into a string with `.stringify`. If the promise is successful, we receive and return the response and call the method `loadRoasters()` which will indexes all the roasters and coffees to the page. Otherwise, if the promise/validation fails then an error will show!

I really had to spend time reviewing the code and going back and forth between pages to get an idea of what was going on and visualize the concept. This was rewarding to see what was going on in Javascript and when things are done asynchronously.

