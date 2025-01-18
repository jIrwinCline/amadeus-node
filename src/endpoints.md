# 1. GET /citySearch
Purpose
Search for city and airport locations based on a keyword.

Query Parameters
Parameter	Type	Description
keyword	String	The search keyword (e.g., city or airport name).
Example Request
http
GET /citySearch?keyword=Paris
Example Response
```
{
  "data": [
    {
      "type": "location",
      "subType": "CITY",
      "name": "Paris",
      "iataCode": "PAR",
      "address": {
        "cityName": "Paris",
        "countryCode": "FR"
      }
    },
    {
      "type": "location",
      "subType": "AIRPORT",
      "name": "Charles de Gaulle Airport",
      "iataCode": "CDG",
      "address": {
        "cityName": "Paris",
        "countryCode": "FR"
      }
    }
  ]
}
```

# 2. POST /date
Purpose
Search for flight offers based on departure and arrival locations and dates.

Request Body
Field	Type	Description
departure	String	Departure date in YYYY-MM-DD format.
arrival	String	Return date (optional) in YYYY-MM-DD format.
locationDeparture	String	IATA code of the departure location.
locationArrival	String	IATA code of the arrival location.
Example Request
```
{
  "departure": "2025-05-01",
  "arrival": "2025-05-10",
  "locationDeparture": "JFK",
  "locationArrival": "LHR"
}
```
Example Response
```
{
  "data": [
    {
      "type": "flight-offer",
      "id": "1",
      "source": "GDS",
      "instantTicketingRequired": false,
      "itineraries": [
        {
          "segments": [
            {
              "departure": {
                "iataCode": "JFK",
                "at": "2025-05-01T20:00:00"
              },
              "arrival": {
                "iataCode": "LHR",
                "at": "2025-05-02T08:00:00"
              }
            }
          ]
        }
      ],
      "price": {
        "currency": "USD",
        "total": "850.00",
        "base": "800.00"
      }
    }
  ]
}
```

# 3. POST /flightprice
Purpose
Validate the pricing of a flight offer.

Request Body
Field	Type	Description
flightOffers	Array	The flight offers object to validate pricing.
Example Request
```
[
  {
    "id": "1",
    "source": "GDS",
    "itineraries": [
      {
        "segments": [
          {
            "departure": {
              "iataCode": "JFK",
              "at": "2025-05-01T20:00:00"
            },
            "arrival": {
              "iataCode": "LHR",
              "at": "2025-05-02T08:00:00"
            }
          }
        ]
      }
    ],
    "price": {
      "currency": "USD",
      "total": "850.00",
      "base": "800.00"
    }
  }
]
```
Example Response
```
{
  "data": {
    "type": "flight-offers-pricing",
    "flightOffers": [
      {
        "id": "1",
        "price": {
          "currency": "USD",
          "total": "850.00",
          "base": "800.00"
        }
      }
    ]
  }
}
```

# 4. POST /flightCreateOrder
Purpose
Create a flight order for a specific flight offer.

Request Body
Field	Type	Description
flightOffer	Object	The flight offer to book.
travelers	Array	Array of traveler information.
Example Request
```
{
  "flightOffer": {
    "id": "1",
    "source": "GDS",
    "itineraries": [
      {
        "segments": [
          {
            "departure": {
              "iataCode": "JFK",
              "at": "2025-05-01T20:00:00"
            },
            "arrival": {
              "iataCode": "LHR",
              "at": "2025-05-02T08:00:00"
            }
          }
        ]
      }
    ]
  },
  "travelers": [
    {
      "id": "1",
      "name": {
        "firstName": "Adriana",
        "lastName": "Gonzales"
      },
      "dateOfBirth": "2012-10-11",
      "gender": "FEMALE",
      "contact": {
        "emailAddress": "adriana.gonzales@example.com",
        "phones": [
          {
            "deviceType": "MOBILE",
            "countryCallingCode": "1",
            "number": "1234567890"
          }
        ]
      }
    }
  ]
}
```
Example Response
```
{
  "data": {
    "type": "flight-order",
    "id": "12345",
    "flightOffers": [
      {
        "id": "1",
        "price": {
          "currency": "USD",
          "total": "850.00"
        }
      }
    ],
    "travelers": [
      {
        "id": "1",
        "name": {
          "firstName": "Adriana",
          "lastName": "Gonzales"
        }
      }
    ]
  }
}
```

# 5. GET /flightcretaeorderget
Purpose
Retrieve the last created flight order.

Query Parameters
None.

Example Request
http
GET /flightcretaeorderget
Example Response
```
{
  "data": {
    "type": "flight-order",
    "id": "12345",
    "flightOffers": [
      {
        "id": "1",
        "price": {
          "currency": "USD",
          "total": "850.00"
        }
      }
    ]
  }
}
```
