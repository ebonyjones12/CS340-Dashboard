# Grazioso Salvare Animal Shelter Dashboard

**Developer:** Ebony Jones
**Course:** CS 340 - Client/Server Development 
**Date:** February 2026

---

## Project Overview

This project is a full-stack web application dashboard developed for Grazioso Salvare, an international rescue animal training company. The dashboard enables users to interact with and visualize data from the Austin Animal Center database to identify dogs that are suitable candidates for various types of search-and-rescue training.

The application follows the **Model-View-Controller (MVC)** design pattern:
- **Model:** MongoDB database
- **View:** Dash components (data table, charts, map)
- **Controller:** Custom CRUD Python module

---

## Required Functionality

The dashboard provides the following features:

- **Interactive Filtering Options:** Radio buttons allow users to filter animals by rescue type (Water Rescue, Mountain/Wilderness Rescue, Disaster/Individual Tracking, and Reset)

- **Interactive Data Table:** A responsive data table with sorting, filtering, pagination, and single-row selection that dynamically updates based on the selected filter

- **Pie Chart Visualization:** A donut chart displaying the distribution of animal breeds within the filtered dataset

- **Geolocation Map:** An interactive Leaflet map showing the location of the selected animal with breed tooltip and name popup

---

## Screenshots

### Water Rescue Filter
Displays dogs with Labrador Retriever, Chesapeake Bay Retriever, and Newfoundland breeds (intact females, 26-156 weeks old).

<img width="1470" height="325" alt="Screenshot 2026-02-21 at 8 53 30 PM" src="https://github.com/user-attachments/assets/87bd9d4f-2239-447c-bb19-b1242d341ae3" />


### Mountain/Wilderness Rescue Filter
Displays dogs with German Shepherd, Alaskan Malamute, Old English Sheepdog, Siberian Husky, and Rottweiler breeds (intact males, 26-156 weeks old).

<img width="1412" height="322" alt="Screenshot 2026-02-21 at 8 53 38 PM" src="https://github.com/user-attachments/assets/08478188-1fe7-4072-8b95-5b45b61a4cc2" />


### Disaster/Individual Tracking Filter
Displays dogs with Doberman Pinscher, German Shepherd, Golden Retriever, Bloodhound, and Rottweiler breeds (intact males, 20-300 weeks old).

<img width="1457" height="333" alt="Screenshot 2026-02-21 at 8 53 45 PM" src="https://github.com/user-attachments/assets/895f2bde-934e-4fd1-8cfc-8314545d771a" />


### Pie Chart and Geolocation Map
The pie chart shows breed distribution and the map displays animal locations in the Austin, Texas region.

<img width="1495" height="407" alt="Screenshot 2026-02-21 at 8 53 57 PM" src="https://github.com/user-attachments/assets/475c1433-3726-4ee2-9939-01ca18c5e0d3" />


---

## Tools Used

### MongoDB (Model)
MongoDB was chosen as the database because it is a document-oriented NoSQL database that stores data in flexible, JSON-like documents. It integrates seamlessly with Python through PyMongo and supports complex filtering operations using regex pattern matching and range queries.

### Dash Framework (View and Controller)
Dash is a Python framework built on Flask, Plotly, and React that enables interactive web applications. It provides built-in components for data visualization and uses a reactive callback system to handle user interactions.

### CRUD Python Module
A custom Python module (`animal_shelter.py`) provides Create, Read, Update, and Delete operations for MongoDB. The module abstracts database logic into reusable methods, promoting maintainability and separation of concerns.

### Additional Libraries
- **Pandas:** Data manipulation and DataFrame conversion
- **Plotly Express:** Interactive chart creation
- **Dash Leaflet:** Geolocation map integration
- **JupyterDash:** Running Dash apps in Jupyter notebooks

---

## Installation and Setup

### Prerequisites
- Python 3.x
- MongoDB server running locally
- Austin Animal Center dataset imported into the `aac` database

### Steps to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/CS340-Dashboard.git
   ```

2. Ensure MongoDB is running and the `aac` database contains the `animals` collection

3. Place these files in the same directory:
   - `ProjectTwoDashboard.ipynb`
   - `animal_shelter.py`
   - `Grazioso Salvare Logo.png`

4. Open the notebook in Jupyter:
   ```bash
   jupyter notebook ProjectTwoDashboard.ipynb
   ```

5. Run the cell to launch the dashboard

6. Use the radio buttons to filter data and click table rows to update the map

---

## Challenges and Solutions

**Challenge 1 - Breed Name Matching:**  
The database contained mixed breed names with slashes (e.g., "German Shepherd/Labrador Retriever"). Solved by using MongoDB regex queries with the `$or` operator to find breeds containing the target breed name.

**Challenge 2 - CRUD Module Parameters:**  
The initial CRUD module didn't accept username/password parameters. Updated the `__init__` method to accept these for secure authentication.

**Challenge 3 - MongoDB ObjectId:**  
The `_id` column caused DataTable crashes due to ObjectId type. Solved by dropping the `_id` column from DataFrames before display.

---

## Project Structure

```
CS340-Dashboard/
├── ProjectTwoDashboard.ipynb    # Main dashboard notebook
├── animal_shelter.py            # CRUD Python module
├── Grazioso Salvare Logo.png    # Company logo
├── README.md                    # This file
└── screenshots/                 # Dashboard screenshots
    ├── water_rescue.png
    ├── mountain_rescue.png
    ├── disaster_rescue.png
    └── chart_map.png
```

---

## Resources

- [Dash Documentation](https://dash.plotly.com/)
- [MongoDB Documentation](https://www.mongodb.com/docs/)
- [PyMongo Documentation](https://pymongo.readthedocs.io/)
- [Dash Leaflet](https://dash-leaflet.herokuapp.com/)
- Austin Animal Center Dataset: City of Austin, Texas Open Data Portal

---

## Reflection

**How do you write programs that are maintainable, readable, and adaptable?**

I focus on writing clean code that separates different responsibilities into their own pieces. The CRUD Python module I built for Project One is a good example of this. Instead of writing database code directly in my dashboard, I created a separate module with methods for create, read, update, and delete operations. This made my code easier to read because anyone looking at the dashboard code can see what it's doing without getting lost in database details. It also made the code adaptable because when I needed to connect the dashboard to MongoDB in Project Two, I just imported the module and called its methods. The CRUD module could easily be reused in other projects too, like a mobile app or a different web interface that needs to work with the same animal shelter database.

**How do you approach a problem as a computer scientist?**

I start by understanding what the client actually needs, then I break the problem down into smaller parts. For the Grazioso Salvare project, I looked at their requirements for finding rescue dogs and figured out what data I needed, how to filter it, and how to display it. This was different from earlier coursework where I might just jump into coding. Here I had to think about the whole system - the database structure, the queries, the user interface, and how everything connects. In the future, I would use this same approach of understanding requirements first, then designing the database schema to match what the client needs, and building modular components that can be tested separately before putting them together.

**What do computer scientists do, and why does it matter?**

Computer scientists solve problems by building tools that help people work smarter. For Grazioso Salvare, they needed a way to quickly find dogs that would be good candidates for different types of rescue training. Without this dashboard, someone would have to manually search through thousands of animal records. Now they can click a button and instantly see all the dogs that match their criteria, along with a map showing where each animal is located. This saves them hours of work and helps them find and train rescue animals faster, which ultimately means more lives saved during disasters and emergencies.

---

## Contact

**Developer:** Ebony Jones  
**Course:** CS 340 - Client/Server Development  
