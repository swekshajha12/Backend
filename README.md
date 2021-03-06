# Backend
Flask server for APIs

1) Clone the repo.

2) Install requirements:	
```
cd Backend
./install.sh
```

3) Run the flask web app: 	
```
python main.py
```
4) Check localhost:		http://localhost:5000 OR http://127.0.0.1:5000


- To initially load your database:
```
curl -i http://localhost:5000/loadDb
```

---------
# APIs

- Retrieve all twitter based traffic based on the route at the particular time, between source and destination.

Sample Data:
```
{
  "src":"mvit",
  "srclat":"40.81381340000001",
  "srclong":"-74.06693179999999",
  "dest":"hebbal",
  "destlat":"40.8145647",
  "destlong":"-74.06878929999999",
  "date":"2016-10-25",
  "time":"13:32:12"
}
```

Example:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"src":"mvit","srclat":"40.81381340000001","srclong":"-74.06693179999999","dest":"hebbal","destlat":"40.8145647","destlong":"-74.06878929999999","date":"2016-10-25","time":"13:32:12"}' http://localhost:5000/api/route/traffic/now
```

- Retrieve all twitter based traffic based on the route (All time), between source and destination.

Sample Data:
```
{
  "src":"mvit",
  "srclat":"40.81381340000001",
  "srclong":"-74.06693179999999",
  "dest":"hebbal",
  "destlat":"40.8145647",
  "destlong":"-74.06878929999999",
}
```

Example:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"src":"mvit","srclat":"40.81381340000001","srclong":"-74.06693179999999","dest":"hebbal","destlat":"40.8145647","destlong":"-74.06878929999999"}' http://localhost:5000/api/route/traffic/alltime
```

- To retrieve all tweets from blrtraffic twitter feed

```curl -i http://localhost:5000/api/blrttweets```

- Retrieve all checkpoint locations that falls in the route between source and destination

Sample Data:
```
{
	"srclat":"40.81381340000001",
	"srclong":"-74.06693179999999",
	"destlat":"40.8145647",
	"destlong":"-74.06878929999999",
}
```
Sample Response:
```
{
  "checkpoints-locations": [
    "2nd Cross Rd, Sector 3, Marathahalli, Bengaluru, Karnataka 560037, India", 
    "HAL Old Airport Rd, Sector 3, Marathahalli, Bengaluru, Karnataka 560017, India", 
    "HAL Old Airport Rd, Jawahar Nagar, Marathahalli, Bengaluru, Karnataka 560037, India", 
    "Doddanekundi Main Rd, Sanjay Nagar, Marathahalli, Bengaluru, Karnataka 560037, India", 
    "Srinagar - Kanyakumari Hwy, Aswath Nagar, Kartik Nagar, Bengaluru, Karnataka 560037, India", 
    "Srinagar - Kanyakumari Hwy, Ferns City, Chinappa Layout, Mahadevapura, Bengaluru, Karnataka 560037, India", 
    "Service Rd, Chinappa Layout, Mahadevapura, Bengaluru, Karnataka 560037, India", 
    "Service Rd, Laxmi Sagar Layout, Mahadevapura, Bengaluru, Karnataka 560037, India", 
    "39/5, Outer Ring Rd, Brindavan Extension, Doddanekkundi, Mahadevapura, Bengaluru, Karnataka 560037, India", 
    "India Tin Industries Ltd., Pai Layout, Mahadevapura, Bengaluru, Karnataka 560016, India", 
    "6/1A, Service Rd, Subramani Nagar, Hebbal Kempapura, Bengaluru, Karnataka 560032, India", 
    "118, Outer Ring Rd, Subramani Nagar, Guddadahalli, Hebbal Kempapura, Bengaluru, Karnataka 560024, India", 
    "2275, Tumkur Main Rd, Yeshwanthpur Industrial Area, Phase 1, Peenya, Bengaluru, Karnataka 560022, India", 
    "2275, Tumkur Main Rd, Yeshwanthpur Industrial Area, Phase 1, Peenya, Bengaluru, Karnataka 560022, India", 
    "20, Tumkur Main Rd, Raja Industrial Estate, Yeshwanthpur, Bengaluru, Karnataka 560022, India", 
    "Bengaluru - Mangaluru Highway, Indiranagar, Nelamangala, Karnataka 562123, India", 
    "Davanagere-Harihar Bypass, Mahajenahalli, Karnataka 577601, India", 
    "Shimoga - Harihar - Hospet Rd, Mahajenahalli, Karnataka 577601, India", 
    "Shimoga - Harihar - Hospet Rd, Devanayakanahalli, Karnataka 577217, India", 
    "Honnalli-Ranebennur Rd, Honnali, Karnataka 577217, India", 
    "Bangalore - Honavar Rd, Ayanur, Karnataka 577211, India", 
    "Bangalore - Honavar Rd, Ayanur, Karnataka 577211, India", 
    "SH 52, Benavalli, Karnataka 577426, India"
  ]
}
```

Example:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"srclat":"40.81381340000001","srclong":"-74.06693179999999","destlat":"40.8145647","destlong":"-74.06878929999999"}' http://localhost:5000/api/checkpoints/locations
```


- Retrieve all checkpoint locations in coordinates that falls in the route between source and destination

Sample Data:
```
{
	"srclat":"40.81381340000001",
	"srclong":"-74.06693179999999",
	"destlat":"40.8145647",
	"destlong":"-74.06878929999999",
}
```
Sample Response:
```
{
  "checkpoints-coordinates": [
    {
      "lat": 12.9563368, 
      "lng": 77.68788119999999
    }, 
    {
      "lat": 12.9552131, 
      "lng": 77.6879663
    }, 
    {
      "lat": 12.9558811, 
      "lng": 77.6917838
    }, 
    {
      "lat": 12.9680119, 
      "lng": 77.6933749
    }, 
    {
      "lat": 12.9680765, 
      "lng": 77.7015955
    }, 
    {
      "lat": 12.9748694, 
      "lng": 77.69745259999999
    },
    .
    .
    .
 ]
}
```

Example:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"srclat":"40.81381340000001","srclong":"-74.06693179999999","destlat":"40.8145647","destlong":"-74.06878929999999"}' http://localhost:5000/api/checkpoints/coordinates
```

- Retrieve all status and tweets

Sample Data:
```
{
  "srclat":"40.81381340000001",
  "srclong":"-74.06693179999999",
  "destlat":"40.8145647",
  "destlong":"-74.06878929999999",
}
```
Sample Response:
```
{
  "response": [
    {
      "negative": 59.310344827586206, 
      "neutral": 37.93103448275862, 
      "positive": 2.7586206896551726
    }, 
    {
      "date": "2016-12-06", 
      "status": "Negative", 
      "time": "03:52:37", 
      "tweet": "Slow moving traffic at Ejipura Jn form Sony signal on IRR, Marathahalli bridge and Ibluru bus stop form 
Agara"
    }, 
    {
      "date": "2016-12-06", 
      "status": "Caution", 
      "time": "13:53:07", 
      "tweet": "Peak hour traffic at Vellara jn towards Anepalya jn, Sagar hospital jn from Dairy circle, Jalahalli cros
s jn from 8th mile jn on Tumkur road"
    }, 
    {
      "date": "2016-12-06", 
      "status": "Positive", 
      "time": "01:21:51", 
      "tweet": "#BCP : 250 #Hoysala are #Alerted and #watching #City #Safe  #Situation is very #normal in #city. https:/
/t.co/TEa5ThwY81"
    }, 

    .
    .
    .
 ]
}
```

Example:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"srclat":"13.0358","srclong":"77.5970","destlat":"12.9592","destlong":"77.6974"}' http://jith.tk:5000/api/trafficStatusAllTime 
```
