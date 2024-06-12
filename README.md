## Airbnb Bookings Analysis project:

---

# Airbnb Bookings Analysis

## Project Description

### Business Context

Since 2008, Airbnb has been a revolutionary platform that allows guests and hosts to connect for unique travel experiences. With millions of listings globally, analyzing the vast amount of data generated can provide valuable insights for business decisions, customer understanding, and marketing strategies. This project aims to explore and analyze the Airbnb dataset to uncover key understandings that can drive business impact.

### Dataset Description

The dataset consists of around 49,000 observations with 16 columns, containing both categorical and numerical data. The columns include information about the listing, host, location, price, availability, and reviews.

### Main Libraries Used

- **Pandas**: For data manipulation and aggregation
- **Matplotlib** and **Seaborn**: For visualization
- **NumPy**: For computationally efficient operations

## Installation

To run the analysis, you need to install the following Python libraries:

```bash
pip install pandas numpy matplotlib seaborn folium
```

## Usage

1. **Clone the Repository**

```bash
git clone https://github.com/sharmaarjun1228/AirBnb-EDA/blob/main/airbnb_eda.ipynb
cd airbnb-bookings-analysis
```

2. **Run the Jupyter Notebook**

Open the Jupyter notebook and run the cells to perform the Exploratory Data Analysis (EDA).

3. **View the Geographical Map**

The geographical map of the listings can be viewed by opening the `airbnb_listings_map.html` file in a web browser.

## Exploratory Data Analysis

The EDA process involves the following steps:

### 1. Distribution of Prices

```python
plt.figure(figsize=(10, 6))
sns.histplot(df['price'], bins=50, kde=True)
plt.title('Distribution of Prices')
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.show()
```

### 2. Room Type Distribution

```python
plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='room_type')
plt.title('Room Type Distribution')
plt.xlabel('Room Type')
plt.ylabel('Count')
plt.show()
```

### 3. Price vs. Room Type

```python
plt.figure(figsize=(10, 6))
sns.boxplot(data=df, x='room_type', y='price')
plt.title('Price vs. Room Type')
plt.xlabel('Room Type')
plt.ylabel('Price')
plt.show()
```

### 4. Reviews per Month vs. Price

```python
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='reviews_per_month', y='price', hue='room_type')
plt.title('Reviews per Month vs. Price')
plt.xlabel('Reviews per Month')
plt.ylabel('Price')
plt.show()
```

### 5. Listings Distribution Across Neighborhoods

```python
plt.figure(figsize=(14, 8))
sns.countplot(data=df, x='neighbourhood_group', order=df['neighbourhood_group'].value_counts().index)
plt.title('Listings Distribution Across Neighborhoods')
plt.xlabel('Neighborhood Group')
plt.ylabel('Count')
plt.xticks(rotation=90)
plt.show()
```

### 6. Correlation Heatmap

```python
plt.figure(figsize=(12, 8))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Heatmap')
plt.show()
```

### 7. Pair Plot

```python
sns.pairplot(df, vars=['price', 'minimum_nights', 'number_of_reviews', 'reviews_per_month', 'calculated_host_listings_count', 'availability_365'], hue='room_type')
plt.show()
```

### 8. Geographical Map

```python
import folium
from folium.plugins import MarkerCluster

m = folium.Map(location=[40.7128, -74.0060], zoom_start=11)
marker_cluster = MarkerCluster().add_to(m)

for index, row in df.iterrows():
    folium.Marker(
        location=[row['latitude'], row['longitude']],
        popup=f"Name: {row['name']}<br>Price: ${row['price']}<br>Room Type: {row['room_type']}<br>Neighborhood: {row['neighbourhood']}",
        tooltip=row['name']
    ).add_to(marker_cluster)

m.save('airbnb_listings_map.html')
m
```

## Insights and Recommendations

Based on the EDA, the following insights and recommendations can be made:

1. **Price Distribution**: Most listings are priced below $500, with a few outliers. This suggests that Airbnb is accessible to a wide range of budgets.
2. **Room Type**: Entire homes/apartments are the most common type, followed by private rooms. Shared rooms are the least common.
3. **Price vs. Room Type**: Entire homes/apartments tend to be more expensive than private or shared rooms.
4. **Reviews per Month**: Listings with more reviews per month tend to have lower prices, indicating a possible trade-off between price and popularity.
5. **Neighborhood Distribution**: Manhattan has the highest number of listings, followed by Brooklyn. This indicates a high demand for accommodations in these areas.

## Conclusion

This project provides a comprehensive exploratory data analysis of Airbnb bookings, uncovering valuable insights that can guide business strategies and decisions. By understanding the distribution of prices, room types, and geographical locations, Airbnb can tailor its services to meet customer needs and optimize its offerings.

## Author

- **Arjun Sharma**
- linkeIn (https://www.linkedin.com/in/arjun-sharma-714914221/)

## License

This project is licensed under the MIT License.

---

