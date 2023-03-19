
# Hotel-Data-Analysis

In this project I analyse the hotel data to find some insight that will help hotel business to improve.
I took data from [Kaggle](https://www.kaggle.com).
Also I attached file in this repository you can download it by quick link here.
:point_right:
[hotel_bookings 2.csv](https://github.com/Engineer-Aman/Hotel-Data-Analysis/files/11010542/hotel_bookings.2.csv)

## Business Problem 
Questions:
1. what are the variables that affect hotels resrvations cancellations? 
2. how can we make hotels reservations cancelled better? 
3. how will hotels be assisted in making pricing and promotonal decisions?

## Analysis Of Data

```ruby
cancelled=df['is_canceled'].value_counts(normalize=True)
print(cancelled)

plt.figure(figsize=(5,4))
plt.title("Reservation Status")
plt.bar(['Not Cancled','Cancled'],df['is_canceled'].value_counts(),color=['cyan','Yellow',])

```

![Screenshot 2023-03-19 150535](https://user-images.githubusercontent.com/126685886/226166305-120c35a4-1754-4fc3-ba4b-95cbaa249779.png)

The bar graph shows the count of reservations that are canceled and those that are not. It is obvious that there are still a significant number of reservations that have not been canceled. There are more than 37% of clients who canceled their reservation, which have a significant impact on the hotels earnings.

```ruby
plt.figure(figsize=(11,4))
axis1=sns.countplot(x='hotel',hue='is_canceled',data=df,palette='Blues')
legend_labels,_=axis1.get_legend_handles_labels()

plt.title("Reservation Status In Hotels",size=20)
plt.xlabel("hotel",size=14)
plt.ylabel("number of reservations",size=14)
plt.show()

```
![Screenshot 2023-03-19 151345](https://user-images.githubusercontent.com/126685886/226166704-08424d6e-0cd9-4f76-8135-d62f46e91e85.png)

In above chart we can see that in comparison to resort hotels, city hotels have more bookings. It’s possible that resort hotels are more expensive than those in city hotels. Also we can see that reservation cancelation is more in city hotels it's more than 50% compare to resort hotel.

```ruby
plt.figure(figsize=(20,8))
plt.title('Average Daily Rate In Resort And City Hotel',fontsize=30)
plt.plot(resort_hotel.index,resort_hotel['adr'],label='Resort Hotel')
plt.plot(city_hotel.index,city_hotel['adr'],label='City Hotel')
plt.legend(fontsize=20)
plt.show()

```

![Screenshot 2023-03-19 151952](https://user-images.githubusercontent.com/126685886/226167053-868546d9-c692-4d0e-af5f-c8abca08a855.png)

The above line graph shows that, on certain days the average daily rate for a city hotel is less than that of resort hotel, and on other days it is even less. It goes without saying that weekends and holidays may sees a rise in resort hotel rates.
