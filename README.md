
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
