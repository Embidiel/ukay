# Ukay (Buyer App)


## What?
Ukay is an e-commerce platform that lets you buy and sell used items relation to fashion.

## Requirements and Goals of the System

### Personal Goals

 1. Learn Websockets
 2. Learn OAuth (3rd party authentication)
 3. Learn about Paymaya Gateway
 4. Learn NextJS
 5. Learn System Design Basics

### Functional Requirements

 - [ ] Users should be able to login to the application using 3rd party
       platforms like Facebook or Google.
 - [ ] Users should be able to see featured items and a search bar at the Home section of the application.
 - [ ]  A user should be able to chat the store for more information about the item/s he or she is interested.
 - [ ]  Online payment should be the only available payment for now.
 - [ ]  A user should be able only to buy an item if she / he has complete user details (Mobile number, First name, Last name, and Delivery address).
 - [ ] A push notification should arrive to the buyer of an item if the item delivery status was updated.
 - [ ]  A push notification should arrive to the buyer & seller if a chat was received.
 - [ ] A seller account cannot be made into a buyer account. The buying and selling power must be separated from each other using different accounts.
 
 
### Non Functional Requirements
 - [ ] Users or specifically buyers must have a real time experience for using the chat service and determining the number of stocks of an item with minimum latency.
 - [ ] Chat message data & number of stocks should be consistent for every user on all devices.
 - [ ] A seller must be a verified store that has the complete requirements by the state

## Application Interface Definition
I considered splitting up this application into different services or a Microservice architecture. I plan to have a set of services for different business purposes. These are the services that I thought of:

 - **Authentication Service**:
 
Handles, of course, the authentication purposes for our application. So what authentication strategy should we use? I chose JSON Web Token (JWT) for this scenario. All different services should share the same JWT Secret.

***APIs:***

    enter(authprovider, userdata)
|Paramname  | Data Type | Default Value
|--|--|--|
| authprovider| String| null|
| userdata| Object| null|
| role |  Integer (FK) | null

> The enter API is a generic API that ***can be used if the user is already registered or not.*** If the user is already registered, just return a valid JWT to the user. If not, register the user using the userdata that has been passed from the client.

***Returns:***
JSON Web Token with a specified expiration that can be stored inside the client side.

    { msg: jwt , status : 1 }

***How do we know if the user is already registered to the application?***
> OAuth or 3rd party authentication services should be able to return their respective ids For example Google, Google should be able to return the Google ID of the user who used the OAuth service. The Google ID will be stored inside our database for verification purposes.

***How do  I know what data will I extract inside the userdata object?***
> From the client side we shall pass a parameter, lets say ***authprovider***. That parameter stores a value like 'Google' or 'Facebook' and dictates the API what properties we shall extract.

 - **Shop Service:**

Handles most of the business logic regarding products, brands, categories. This service requires an authentication (JWT).

***APIs:***

    getFeaturedProducts (skip, limit)
|Paramname  | Data Type | Default Value
|--|--|--|
| skip| Integer| null|
| limit| Integer| 5|

> Get the list of featured products that shall be displayed at the home page of our shop.

***Returns:***

    [
	    {
		    brand : 'Gucci',
		    productname : "GUCCI Bag",
		    producttag: `gucci-bag`,
		    category: {
			    categoryname : `Bags`,
			    categoryimage : `https://google.com/bag1.png`
		    },
		    averating : 4.9,
		    noofreviews: 129,
		    price: 15490,
		    desc: `Hello world`,
		    saleprice: 10200,
		    percentoff: 5,
		    mainphoto: `https://google.com/img1.png`
	    }
    ]

***What products should we display at this API?***
> Products that are the most rated / most reviewed.
---

    getProduct (producttag)
    
   > Just basically gets all the information regarding the product.

***Returns***

  
	{
			brand: 'Gucci',
		    productname : "GUCCI Bag",
		    producttag: `gucci-bag`,
		    return: 7,
		    warranty : 10,
		    color : {
			    colorname: `Red`,
			    shadehex: `#FF0000`
			},
		    category: {
			    categoryname : `Bags`,
			    categoryimage : `https://google.com/bag1.png`
		    },
		    reviewrating: {
			    noofreviews: 101,
			    averating: 4.2,
			    ratingbreakdown: {
				    5star: 2,
				    4star: 9,
				    3star: 4,
				    2star: 20,
				    1star: 101
			    }
		    },
		    price: 15490,
		    desc: `Hello world`,
		    saleprice: 10200,
		    percentoff: 5,
		    stocks: 10,
		    variations: [
			    {
				    productname: "GUCCI Bag Red",
				    photos: [
				      `https://google.com/image1.png`,
					  `https://google.com/img2.jpg`
				    ],
				    sizes: [
					    {
						  sizename: `Medium`,
						  sizecode: `M`,
						  stocks: 5
					    },
					    {
						  sizename: `Large`,
						  sizecode: `L`,
						  stocks: 5
					    }
					],
		    ],
		    instock: true,
		    seller: {
			    sellername: `GUCCI`,
			    rating: 4.1,
			    sellertag : `gucci`,
			    location: `Laguna`
		    },
		    photos: [
			    `https://google.com/image1.png`,
			    `https://google.com/img2.jpg`
		    ]
	}
    
		 
---

    getFeaturedCategories (skip, limit)
|Paramname  | Data Type | Default Value
|--|--|--|
| skip| Integer| null|
| limit| Integer| 10|

> Get the list of featured categories that shall be displayed at the home page of our shop.

***Returns***

    [
	    {
		    categoryname: `Bags`,
		    categorytag: `bags`,
		    categoryimage: `https://google.com/bag1.jpg`
	    },
	    {
		    categoryname: `Shoes`,
		    categorytag: `shoes`,
		    categoryimage: `https://google.com/shoes1.png`
	    }
    ]

***What categories should we display at this API?***
>  Categories that have the most product reviews and stars / ratings under it.

---

    getProductReviews (producttag, limit, skip, sort, filter)
> Gets a paginated product reviews of a specified product using the ***producttag***.

|Paramname  | Data Type | Default Value
|--|--|--|
| skip| Integer| null|
| limit| Integer| 10|
| sort| String| `sort/high-low`|
| filter| Integer| `filter/reviews/all-star`|

***Returns***

    {
	    totalitems: 10,
	    perpage: 5,
	    noofpages: 5,
	    firstpage: 1,
	    lastpage: 5,
	    currpage: 3,
	    items: [
		    {
			    sender: `John D` <LAST NAME IS HIDDEN>,
			    photos: [
				    `https://google.com/r1.jpg`,
				    `https://google.com/r2.jpg
			    ],
			    rating: 3,
			    datecreated: 2010/10/23
		    },
		    {
			    sender: `Mary A` <LAST NAME IS HIDDEN>,
			    photos: [
				    `https://google.com/r1.jpg`,
				    `https://google.com/r2.jpg
			    ],
			    rating: 5,
			    datecreated: 2010/10/23
		    }
	    ]
    }

***What sort types and filter types should we accept at this API?***
>  Sort : `sort/high-low`, `sort/low-high`, `sort/latest`
> Filter: `filter/reviews/all-star`, `filter/reviews/5-star` to `filter/reviews/1-star`

---

    getBrands (limit, skip)
> Gets all the brands.

|Paramname  | Data Type | Default Value
|--|--|--|
| skip| Integer| null|
| limit| Integer| null|

***Returns***

    [
	    {
		    brandname : `Adidas`,
		    brandtag : `adidas`
	    },
	    {
		    brandname : `Nike`,
		    brandtag : `nike`
	    }
    ]
---

    getProducts (name, category, size, brand, color, sortby, pricestart, priceend)
