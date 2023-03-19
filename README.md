
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

```ruby
df['month']=df['reservation_status_date'].dt.month
plt.figure(figsize=(16,8))
ax=sns.countplot(x='month',hue='is_canceled',data=df,palette='Reds')
legend_labels,_=ax.get_legend_handles_labels()
ax.legend(bbox_to_anchor=(1,1))
plt.title("Reservation Status Per Month",size=20)
plt.xlabel("Month",size=14)
plt.ylabel("number of reservations",size=14)
plt.legend(['not canceled','canceled'])
plt.show()

```

![4](https://user-images.githubusercontent.com/126685886/226167374-c229b79a-7440-4798-80c8-9d396318cb78.png)

In the above chart we have developed the grouped bar graph to analyze the months with the highest and lowest reservation levels according to reservation status. As can be seen both the number of confirmed reservations and the number of canceled reservations are largest in the month of august. Whereas January is the month with the most canceled reservations.

```ruby
plt.figure(figsize=(16,8))
plt.title('Canceled ADR Per Month', fontsize=20)
sns.barplot('month','adr',data=df[df['is_canceled']==1].groupby('month')[['adr']].sum().reset_index())
plt.xlabel("Month",size=14)
plt.ylabel("ADR",size=14)
plt.show()

```
![5](https://user-images.githubusercontent.com/126685886/226167881-176e0d2e-c757-4c16-b650-1e433834c53c.png)

This bar graph demonstrates that cancellations are most common when prices are greatest and are least common when they are lowest. Therefore, the cost of the accommodation is solely responsible for the cancellation.

```ruby
can_data=df[df['is_canceled']==1]
top_10=can_data['country'].value_counts()[:10]
plt.figure(figsize=(7,7))
plt.title("Top 10 Country With Reservation Canceling")
plt.pie(top_10,autopct='%.2f', labels=top_10.index)
plt.show()

```
![6](https://user-images.githubusercontent.com/126685886/226168013-8807c382-1ddd-4201-bc62-3a269c0ebb1e.png)

In above chart we try to demonstrate the top 10 countries with the highest reservation cancelations. We can see that Portugal have a highest reservation cancelation that are 68.91% rather other country.

```ruby
plt.figure(figsize=(10,4))
plt.title("Reservation Status")
plt.bar(['Online TA','Offline TA/TO','Groups','Direct','Corporate','Complementary','Aviation']
        ,df['market_segment'].value_counts(),color=['Violet', 'pink'])
        
```

![7](https://user-images.githubusercontent.com/126685886/226168301-474a87ea-6d3a-4baa-a6b2-f4e66c096a86.png)

In above chart we can see which market segment have highest and lowest hotel reservation. In it we can see that highest hotels reservation done by online travel agent and then next offline travel agent and travel organization so it highest chances that there reservation cancellation are high.

```ruby
plt.figure(figsize=(16,8))
ax=sns.countplot(x=df['market_segment'],hue='is_canceled',data=df,palette='Greens')
legend_labels,_=ax.get_legend_handles_labels()
ax.legend(bbox_to_anchor=(1,1))
plt.title("Reservation Status by segment",size=20)
plt.xlabel("Segment",size=14)
plt.ylabel("number of reservations",size=14)
plt.legend(['not canceled','canceled'])
plt.show()

```

![8](https://user-images.githubusercontent.com/126685886/226171467-dd40f6a9-02b1-484d-b4ef-a18c5032d93e.png)

In above chart we can observe the reservation status by segment. We can see that online travel agent have highest reservation number where in it more than 50% reservations get canceled by them. Also we can observe that after Online TA, offline TA/TO have highest reservation number and in it near 40% of reservation get canceled. In the entire segment Aviation segment have less number of reservation.
