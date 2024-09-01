Simplified Airline Booking System
This is a Django-based API application for managing a simplified airline booking system. 
The project demonstrates the use of Django REST Framework to create and manage API endpoints for flights and passengers.

Table of Contents
Installation
Project Setup
Running the Server
API Endpoints
Models
Serializers
ViewSets
Design Decisions
Optional Enhancements
Installation
To set up this project locally, follow the steps below:

Prerequisites
Python 3.7+
pip
Virtual environment (optional but recommended)
Step 1: Clone the Repository
sh
Copy code
git clone https://github.com/YOUR-USERNAME/airline_booking_system.git
cd airline_booking_system
Step 2: Create and Activate a Virtual Environment
sh
Copy code
python -m venv myenv
source myenv/bin/activate   # On macOS/Linux
myenv\Scripts\activate      # On Windows
Step 3: Install Dependencies
sh
Copy code
pip install -r requirements.txt
Step 4: Apply Migrations
sh
Copy code
python manage.py makemigrations
python manage.py migrate
Project Setup
Step 1: Create a Superuser
To access the Django admin, you'll need to create a superuser:

sh
Copy code
python manage.py createsuperuser
Step 2: Run the Development Server
Start the Django development server:

sh
Copy code
python manage.py runserver
You can now access the project at http://127.0.0.1:8000/.

API Endpoints
Here are the main API endpoints provided by this application:

Flights:

GET /api/flights/ - List all flights
POST /api/flights/ - Create a new flight
GET /api/flights/{id}/ - Retrieve details of a specific flight
PUT /api/flights/{id}/ - Update a specific flight
DELETE /api/flights/{id}/ - Delete a specific flight
Passengers:

GET /api/passengers/ - List all passengers
POST /api/passengers/ - Create a new passenger
GET /api/passengers/{id}/ - Retrieve details of a specific passenger
PUT /api/passengers/{id}/ - Update a specific passenger
DELETE /api/passengers/{id}/ - Delete a specific passenger
Models
Flight Model
The Flight model represents a flight in the airline system. It includes the following fields:

flight_number: A unique identifier for the flight.
departure: The date and time of departure.
arrival: The date and time of arrival.
origin: The origin airport.
destination: The destination airport.
capacity: The total number of seats available on the flight.
Passenger Model
The Passenger model represents a passenger in the system. It includes the following fields:

first_name: The first name of the passenger.
last_name: The last name of the passenger.
email: A unique email address for the passenger.
phone_number: The contact number of the passenger.
flight: A ForeignKey linking the passenger to a specific flight.
Serializers
FlightSerializer
The FlightSerializer is responsible for converting the Flight model instances into JSON format for API responses and vice versa. It includes all the fields of the Flight model.

PassengerSerializer
The PassengerSerializer converts Passenger model instances into JSON format and vice versa. It also includes details of the related Flight.

ViewSets
FlightViewSet
The FlightViewSet handles CRUD operations for the Flight model. It supports listing, retrieving, creating, updating, and deleting flights.

PassengerViewSet
The PassengerViewSet handles CRUD operations for the Passenger model. It supports listing, retrieving, creating, updating, and deleting passengers.

Design Decisions
Model Relationships:

The relationship between Flight and Passenger is a one-to-many relationship, where one flight can have multiple passengers, but each passenger is associated with exactly one flight.
ViewSets:

Django REST Framework's ModelViewSet was chosen for simplicity and to leverage built-in functionalities like automatic URL routing, request parsing, and response rendering.
Serializers:

ModelSerializer was used for both models to quickly generate serializers based on the model definitions. This provides a straightforward way to manage data validation and conversion between Python objects and JSON.
Validation:

Basic validation is handled by Django and Django REST Framework. For example, unique constraints on fields like flight_number and email ensure data integrity.
Optional Enhancements
Consider adding the following features to improve the functionality:

Filtering: Implement filtering options in the viewsets, such as filtering passengers by flight.
Pagination: Implement pagination for the list endpoints to handle large datasets efficiently.
Authentication: Add authentication to secure the API and manage user access.
Rate Limiting: Implement rate limiting to prevent abuse of the API.
License
This project is licensed under the MIT License.
