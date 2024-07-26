# Data-analysis-of-mavenmovie-data-set
I have performed data analysis on maven movies dataset by using MySQL, SQL scripts, Excel, Pivot tables, Visualizations and made a final report in a PPT file

Objective: To analyze rental trends, identify popular films, and assess store performance using the MavenMovies Sakila database.
Tasks:
1. Rental Trends:
Analyze the monthly rental trends over the available data period.
Determine the peak rental hours in a day based on rental transactions.

2. Film Popularity:	
Identify the top 10 most rented films.
Determine which film categories have the highest number of rentals.

3. Store Performance:
Identify which store generates the highest rental revenue.
Determine the distribution of rentals by staff members to assess performance.

I used the following SQL scripts to extract the required data from the maven-movies dataset.

## 1. Rental Trends:

Analyze the monthly rental trends over the available data period.

## SQL Code
select date_format(rental_date,'%m-%Y') as monthly_rental_date, count(rental_id) as rental_count from rental group by monthly_rental_date;
After extracting the data to Excel, I inserted a pivot table and made graphical presentations which shows monthly rental trends
![image](https://github.com/user-attachments/assets/7e714010-fa21-4120-96b4-6a9ceda5b676)

Determine the peak rental hours in a day based on rental transactions.

## SQL Code
select date_format(rental_date,’%H') as hourly_rental, count(rental_id) as rental_count from rental group by hourly_rental;

After extracting the data to Excel, I inserted a pivot table and made graphical presentations which shows hourly rental trends
![image](https://github.com/user-attachments/assets/a6ec0d99-c3f6-4e6e-9fb9-475e6e9b21a9)

## 2. Film Popularity:	

Identify the top 10 most rented films.

## SQL Code
select film.film_id,title,count(rental_id) as rental_count from film
inner join inventory on film.film_id=inventory.film_id
inner join rental
on inventory.inventory_id=rental.inventory_id
group by film_id,title
order by rental_count desc limit 10;

After extracting the data to Excel, I inserted a pivot table and made graphical presentations which show the top 10 most rented films.
![image](https://github.com/user-attachments/assets/9eeac2dc-a3c3-4a99-8cca-bed361b83f5f)



Determine which film categories have the highest number of rentals.

## SQL Code
select name,count(rental_id) as rental_count from category
inner join film_category
on category.category_id=film_category.category_id
inner join inventory
on film_category.film_id=inventory.film_id
inner join rental
on inventory.inventory_id=rental.inventory_id
group by name
order by rental_count desc;

After extracting the data to Excel, I inserted a pivot table and made graphical presentations which show film categories have the highest number of rentals.
![image](https://github.com/user-attachments/assets/6c70ec1e-b3be-4b8a-a030-171d74df93ce)


## 3. Store Performance:

Identify which store generates the highest rental revenue.

## SQL Code
select store.store_id,sum(amount) from store
inner join inventory
on store.store_id=inventory.store_id
inner join rental
on inventory.inventory_id=rental.inventory_id
inner join payment
on rental.rental_id=payment.rental_id
group by store_id


After extracting the data to Excel, I inserted a pivot table and made graphical presentations which shows store that generates the highest rental revenue
![image](https://github.com/user-attachments/assets/cfdd8769-1e2c-4c5b-9c76-3e5dad0cf883)


Determine the distribution of rentals by staff members to assess performance.

## SQL Code
select rental.staff_id,count(rental.rental_id) from rental
inner join payment
on rental.rental_id=payment.rental_id
group by staff_id



After extracting the data to Excel, I inserted a pivot table and made graphical presentations which show  distribution of rentals by staff members to assess performance.
![image](https://github.com/user-attachments/assets/6c416ea7-65b9-4b49-973b-cc819dd4cfef)












