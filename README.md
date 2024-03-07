# Excel Sales Project


## Table of Contents

* [Problem Statement](#problem-statement)
* [Data Sourcing](#data-sourcing)
* [Data Presentation](#data-presentation)
* [Data Analysis](#data-analysis)
* [Insights](#insights)
- - - -
### Problem Statement

The purpose of this analysis is to provide a sales report per customer and country for the CEO of the company.

About:
* Transactions
* Profit
* Brands
* Products
* Regions


- - - -
### Data Sourcing

The Dataset used for this analysis is a fictional dataset  and is available in the file above.

- - - -

### Data Presentation

> * The Dataset has 6 tables, with 10.281 customers, 24 stores in three countries and 1560 products.
> * The transactions were processed from 1/1/1997 until 31/12/1998.
> * Data Cleaning is done by importing the dataset with Power Query and Transform the data.


#### Diagram View

  > * After importing the data with Power Query, we Transform the data(checking: data types, headers names, text-columns adjustments,dates-column format)
  > and finally we Load the data to the Data Model.
  >
  > * Organize the tables in a relational database based on primary and foreign keys, by creating table relationships.
  >   
  > * Extract the Diagram View that follows.

 ![Diagram View](https://github.com/RoulaNtinou/Excel/blob/2e9fdf2b83f882ebcde8f1467f514701958ae909/DiagramView.png)

- - - -
### Data Analysis


1. >  The transactions have increased more than 100% the second year and this is due to 11 stores bought by the company at the beginning of 1998.
 
  
  ![Transactions per Year](https://github.com/RoulaNtinou/Excel/blob/313b0f92253cd9068bee5cbe1cda1a0cd5a38dc2/Transactions.png)


2. > The new stores bought at the beginning of 1998, are outside USA, and more specifically in Mexico and Canada.	


  ![Profit](https://github.com/RoulaNtinou/Excel/blob/7d964af56d42ffde0bc633d8eae04b90264ad6b0/Profit.png)
 


3. > Follow the top ten brands based on the profit gained.

 ![Top10 Brands](https://github.com/RoulaNtinou/Excel/blob/0d05a8976dbf2d366a9c9284a5e38c57c743d726/Top10Brands.png)
  
  
 



4.	




5.	We are interested in how diverse your film offering is as a means of understanding how likely 
you are to keep customers engaged in the future. Please provide a count of **unique film titles** 
you have in inventory at each store and then provide a count of the unique categories of films you provide. 

``` sql
Select 
     store_id, 
     count(distinct film_id) as 'Unique films'
From inventory
Group by store_id;


Select 
     count(distinct name) as 'Categories'
From category;
```

| store_id   | Unique films   | 
| ---------  |:-------------: |
| 1          | 792            |
| 2          | 769            |


> The number of categories is 16.


6.	We would like to understand the **replacement cost** of your films. 
Please provide the replacement cost for the film that is least expensive to replace, 
the most expensive to replace, and the average of all films you carry. ``	
``` sql
Select 
       avg(replacement_cost) As 'Avg Replacement Cost',
       min(replacement_cost) As 'Min Replacement Cost',
       max(replacement_cost) As 'Max Replacement Cost'
from film;
```
 

> Avg Replacement Cost        19.984   
> Min Replacement Cost         9.99     
> Max Replacement Cost        29.99      


7.	We are interested in having you put **payment** monitoring systems and maximum payment 
processing restrictions in place in order to minimize the future risk of fraud by your staff. 
Please provide the average payment you process, as well as the maximum payment you have processed.
``` sql

Select 
     avg(amount), 
     max(amount)
From payment;
```
> The average payment is 4.2
> The maximum payment is 11.99



8.	We would like to better understand what your customer base looks like. 
Please provide a list of all customer identification values, with a count of **rentals** 
they have made all-time, with your highest volume customers at the top of the list.
``` sql
Select 
     customer_id,count(rental_id) As 'total rentals'
From rental
Group by customer_id
Order by count(rental_id) desc
```

> The highest rental per customer is 46.



9. My partner and I want to come by each of the stores in person and meet the **managers**. 
Please send over the managers’ names at each store, with the full address 
of each property (street address, district, city, and country please). 
 

``` sql
Select  
     first_name, 
     last_name, 
     address, 
     district, 
     city, 
     country
From store
Left Join staff ON store.manager_staff_id=staff.staff_id
Left Join address ON staff.address_id=address.address_id
Left Join city ON address.city_id= city.city_id
Left Join country ON city.country_id= country.country_id;
```
> The managers at each store are: 

| first_name    | last_name  |  address              |  district | City       |  Country  |
|:-------------:| -----:     | ------------------:   | -----:    | -----:     | -----:    |
| Mick          | Hillyer    | 23 Workhaven Lane     | Alberta   | Lethbridge | Canada    |
| Jon           | Stephens   | 1411 Lillydale Drive  | QLD       | Woodridge  | Australia |



10.	I would like to get a better **understanding of all of the inventory** that would come along with the business. 
Please pull together a list of each inventory item you have stocked, including the store_id number, 
the inventory_id, the name of the film, the film’s rating, its rental rate and replacement cost. 

``` sql
Select  
	  inventory.store_id,
    inventory.inventory_id, 
    title, 
    rating,
    rental_rate, 
    replacement_cost
From inventory
Left Join film ON inventory.film_id= film.film_id;
```

> All the inventory items with the rating, rental rate  and replacemnt cost


11.	From the same list of films you just pulled, please roll that data up and provide a summary level overview 
of your inventory. We would like to know how many inventory items you have with each **rating** at each store. 

``` sql
Select  
    store_id, 
    rating,
    count(inventory_id) As 'Number of inventory items'
From inventory
Left Join film ON inventory.film_id= film.film_id
Group by store_id, rating;
```

> All the inventory items per rating at each store.

 
12. Similarly, we want to understand how diversified the inventory is in terms of **replacement cost**. We want to 
see how big of a hit it would be if a certain category of film became unpopular at a certain store.
We would like to see the number of films, as well as the average replacement cost, and total replacement cost, 
sliced by store and film category. 

``` sql
Select 
      store_id,
      category.name As 'Category', 
      count(inventory.inventory_id) As 'Number of films', 
      avg(replacement_cost) As 'Average replacement cost',
	    Sum(replacement_cost) As 'Total replacement cost'
From inventory
Left Join film ON film.film_id=inventory.film_id
Left Join film_category ON film.film_id=film_category.film_id
Left Join category ON film_category.category_id=category.category_id

Group by store_id, name
Order by Sum(replacement_cost) desc;
```

> All the items at each store per film category and in ascending order accoring to the total replacement cost.
> Sports category are at the top of the list.




13.	We want to make sure you folks have a good handle on **who your customers are**. Please provide a list 
of all customer names, which store they go to, whether or not they are currently active, 
and their full addresses – street address, city, and country. 


``` sql
Select 
     first_name, 
     last_name, 
     store_id, 
     active, 
     address, 
     city, 
     country
From customer
Left Join address ON customer.address_id=address.address_id
Left Join city ON address.city_id= city.city_id
Left Join country ON city.country_id=country.country_id;
```

> All the customers with their full addresses. 
> There is a big variety in the origin of customers



14.	We would like to understand how much your **customers are spending** with you, and also to know 
who your most valuable customers are. Please pull together a list of customer names, their total 
lifetime rentals, and the sum of all payments you have collected from them. It would be great to 
see this ordered on total lifetime value, with the most valuable customers at the top of the list. 

``` sql
Select 
     first_name, 
     last_name, 
     count(rental.rental_id) As 'Total rentals', 
     sum(amount) As 'Total Amount'
From customer
Left join rental ON customer.customer_id= rental.customer_id
Left join payment ON rental.rental_id= payment.rental_id
Group by customer.customer_id
Order by  sum(amount) desc;
```
>  The 599 customers have paid from 50 to 221 USD so far.





15. My partner and I would like to get to know your **board of advisors and any current investors**.
Could you please provide a list of advisor and investor names in one table? 
Could you please note whether they are an investor or an advisor, and for the investors, 
it would be good to include which company they work with. 

``` sql
Select 
     'Advisor' As type, 
     first_name, 
     last_name, 
     'Board of Advisors' As 'Company Name'
From advisor
 
 Union
 
Select 
     'Investor' As type, 
     first_name, 
     last_name, 
     company_name
From investor;
```

| type          | first_name  |  last_name     | company_name           |
|:-------------:| -----:      | -----------:   | --------------:        |
|  Advisor      | Barry       |  Beenthere     | Board of Advisors      | 
|  Advisor      | Cindy       |  Smartypants   | Board of Advisors      |
|  Advisor      | Mary        |  Moneybags     | Board of Advisors      |
|  Advisor      | Walter      |  White         | Board of Advisors      |
|  Investor     | Montgomery  |  Burns         | Springfield Syndicators|
|  Investor     | Anthony     |  Stark         | Iron Investors         |
|  Investor     | William     |  Wonka         | Chocolate Ventures     |



16. We're interested in how well you have covered the **most-awarded actors**. 
Of all the actors with three types of awards, for what % of them do we carry a film?
And how about for actors with two types of awards? Same questions. 
Finally, how about actors with just one award? 




``` sql
Select 
   Case 
      When actor_award.awards like '%,%,%' Then 'Three Awards'
      When actor_award.awards like '%,%' Then 'Two Awards'
      Else 'One Award'
   End As 'Number of Awards',
   Avg (Case When actor_award.actor_id IS NULL Then 0 Else 1 END) As '% of Actors with Films'
From actor_award
    
Group by
   Case 
      When actor_award.awards like '%,%,%' Then 'Three Awards'
      When actor_award.awards like '%,%' Then 'Two Awards'
      Else 'One Award'
   End; 
```

| Number of Awards  | % of Actors with Awards   | 
| :-------------:   | :----------------------:  |
| Three Awards      | 0.5714                    |
| Two Awards        | 0.9242                    |
| One Awards        | 0.8333                    |



### Insights

