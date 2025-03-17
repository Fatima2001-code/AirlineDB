# AirlineDB
A Comprehensive MongoDB-Based Flight Management System
![MongoDB Logo](images/Mongodb-Icon.png)
## **Introduction**

In the rapidly growing world of data, where information flows at unprecedented speeds, there is a critical need for robust tools to organize, analyze, and extract knowledge. This is where **MongoDB**, a flexible and scalable document-based database system, comes into play, offering innovative solutions for managing complex datasets.

This project, **AirlineDB**, aims to explore the capabilities of MongoDB in building a flight management application designed to simplify trip planning and organization for travelers, whether individuals or groups. The goal is to meet the diverse needs of travelers by providing an easy-to-use database and advanced features.

### **Challenges Addressed**
- **Information Overload:** The abundance of online information makes it difficult for travelers to find accurate and reliable details about destinations, transportation options, accommodations, and activities.
- **Planning Complexity:** Successful trip planning requires precise coordination between various aspects such as booking flights, accommodations, transportation, and activities, which can be time-consuming and effort-intensive.

We will use **MongoDB (Compass & Shell)** to create a robust and scalable database for storing flight-related data. Along the way, we will face challenges such as:
- Designing an efficient database that meets the application's diverse needs while maintaining performance and efficiency.

---

## **Database Design**

To ensure efficiency and performance, the **AirlineDB** database has been designed with the following eight collections:

### **1. Flights**
- **Description:** Represents all flights offered by the airline.
- **Fields:**
  - `FlightID` (ObjectId): Unique identifier for each flight.
  - `flightCode` (String): Assigned flight code.
  - `departureHour` (Date): Departure time.
  - `arrivalHour` (Date): Arrival time.
  - `flightDay` (Date): Flight date.
  - `price` (Int32): Ticket price.
  - `linkId` (ObjectId): Reference to the `Links` collection.
  - `Notes` (String): Additional notes about the flight.

### **2. Reservations**
- **Description:** Tracks all ticket reservations for flights.
- **Fields:**
  - `departureID` (String): Reference to the `Departures` collection.
  - `passengerID` (ObjectId): Reference to the `Passengers` collection.
  - `price` (Int32): Price paid for the ticket.
  - `discount` (Int32): Applied discount.
  - `done` (Boolean): Indicates whether the reservation is confirmed.
  - `Note` (String): Additional notes.

### **3. Links**
- **Description:** Defines all flight routes offered by the airline.
- **Fields:**
  - `LinkId` (ObjectId): Unique identifier for each route.
  - `departureCity` (String): Departure city name.
  - `arrivalCity` (String): Arrival city name.
  - `Notes` (String): Additional notes.

### **4. PlaneTypes**
- **Description:** Stores details about aircraft types.
- **Fields:**
  - `PlaneTypeID` (ObjectId): Unique identifier for each aircraft type.
  - `planeTypeName` (String): Aircraft type name (e.g., Boeing 737).
  - `brand` (String): Manufacturer’s brand (e.g., Airbus).
  - `capacity` (Int32): Passenger capacity.
  - `weight` (Double): Maximum weight (in kilograms).
  - `length` (Double): Aircraft length (in meters).
  - `nbhoursMaintenance` (Int32): Required maintenance hours.
  - `Note` (String): Additional notes.

### **5. Planes**
- **Description:** Tracks all aircraft owned by the airline.
- **Fields:**
  - `PlaneTypeID` (ObjectId): Reference to the `PlaneTypes` collection.
  - `PlaneName` (String): Unique aircraft name.
  - `planeStartDate` (Date): Date the aircraft was commissioned.
  - `Note` (String): Additional notes.

### **6. Captains**
- **Description:** Manages pilot information.
- **Fields:**
  - `PlanTypeID` (ObjectId): Reference to the `PlaneTypes` collection.
  - `captainName` (String): Pilot’s full name.
  - `captainBirthDate` (Date): Pilot’s birthdate.
  - `captainGender` (String): Pilot’s gender.
  - `captainStartDate` (Date): Date the pilot joined the airline.
  - `lastMedicalExamDate` (Date): Date of the last medical exam.
  - `Note` (String): Additional notes.

### **7. Passengers**
- **Description:** Stores passenger details.
- **Fields:**
  - `passengerName` (String): Passenger’s full name.
  - `passengerAddress` (String): Passenger’s address.
  - `CityID` (ObjectId): Reference to the city.
  - `passengerBirthDate` (Date): Passenger’s birthdate.
  - `Note` (String): Additional notes.

### **8. Departures**
- **Description:** Tracks actual flight departures.
- **Fields:**
  - `_id` (ObjectId): Unique identifier for each departure.
  - `FlightID` (String): Reference to the `Flights` collection.
  - `CaptainID` (ObjectId): Reference to the `Captains` collection.
  - `DepartureHour` (String): Actual departure time.
  - `ArrivalHours` (String): Expected arrival time.
  - `Note` (String): Additional notes.

---

## **Indexing for Performance**

Indexes are crucial in MongoDB to improve query performance. Below are the proposed indexes for **AirlineDB**:

| Collection    | Field(s)              | Reason                                                                 |
|---------------|-----------------------|------------------------------------------------------------------------|
| **Planes**    | `planeTypeId`         | Links pilots to the aircraft they are qualified to fly.               |
| **Captains**  | `planeType`           | Links captains to the aircraft types they are qualified to operate.   |
| **Passengers**| `passengerName`, `CityID` | Improves search speed when looking up passengers by name and city.    |
| **Departures**| `CaptainID`, `PlaneID`| Links flights to assigned captains and aircraft.                      |
| **Reservations**| `passengerId`, `price` | Tracks reservations based on passenger ID and ticket price.           |

---

## **Role-Based Access Control**

Different roles have been defined to ensure secure access to the database:

### **1. System_Administrator**
- **Responsibilities:** Full administrative control over the system.
- **Permissions:** Create, modify, and delete users and data; manage permissions.

### **2. Trip_Admin**
- **Responsibilities:** Manage flight schedules, assign aircraft and captains, handle reservations.
- **Permissions:** Access flight schedules, modify reservations.

### **3. Content_Admin**
- **Responsibilities:** Manage website content, optimize SEO, analyze website data.
- **Permissions:** Create and modify website content.

### **4. Operations_Manager**
- **Responsibilities:** Oversee daily operations, manage staff, improve processes.
- **Permissions:** Access all company data, manage budgets, implement strategies.

---

## **Key Queries**

### **1. Captains & Planes**
Lists captains along with the types of aircraft they are qualified to fly.

### **2. Passengers & Cities & SumOfPrice**
Displays passenger names, cities, and total payments made.

### **3. NumOfPassengersOn_ABB20**
Counts the number of passengers booked on flight "ABB20".

---

## **How to Run the Project**

1. Clone the repository:
   ```bash
   git clone https://github.com/Fatima2001-code/AirlineDB.git
   cd AirlineDB
   

## **Conclusion**
The AirlineDB project represents a significant advancement in flight management systems, leveraging MongoDB's flexibility and scalability to address modern aviation challenges. By providing a robust, secure, and efficient database solution, this project empowers airlines to enhance customer experiences, streamline operations, and drive financial performance.

🚀 Thank you for exploring AirlineDB! Together, let's redefine the future of air travel. 🚀
