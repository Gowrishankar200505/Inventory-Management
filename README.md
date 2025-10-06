# inventory_management_system
A comprehensive inventory management web application built with Flask, implementing all requirements from the Flask hiring test.

Deployed Link: https://inventory-management-hlc5.onrender.com/
Features
Product Management: Add, edit, and view products with unique IDs
Location Management: Manage warehouse and storage locations
Movement Tracking: Record product movements with three types:
Incoming stock (from external sources)
Outgoing stock (sales, shipments)
Inter-location transfers
Balance Report: Real-time inventory balance across all locations
Professional UI: Bootstrap-based responsive design
Form Validation: Comprehensive input validation and error handling
Screenshots
Dashboard
Dashboard

Products
Products

Locations
Locations

Movements
Movements

Balance Report
Balance Report

Balance Report

Database Schema
Product Table
product_id (Primary Key, String)
name (String, Required)
description (Text, Optional)
Location Table
location_id (Primary Key, String)
name (String, Required)
description (Text, Optional)
ProductMovement Table
movement_id (Primary Key, Auto-increment)
timestamp (DateTime, Auto-generated)
from_location (Foreign Key to Location, Nullable)
to_location (Foreign Key to Location, Nullable)
product_id (Foreign Key to Product, Required)
qty (Integer, Required)
Installation & Setup
Clone or download the project files

Create a virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install dependencies:

pip install -r requirements.txt
Run the application:

python app.py
Access the application: Open your browser and go to http://localhost:5000

Project Structure
flask-inventory/
│
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── inventory.db          # SQLite database (created automatically)
├── README.md             # This file
│
└── templates/            # Jinja2 templates
    ├── base.html         # Base template with navigation
    ├── dashboard.html    # Dashboard with statistics
    ├── products.html     # Product listing
    ├── add_product.html  # Add new product form
    ├── edit_product.html # Edit product form
    ├── locations.html    # Location listing
    ├── add_location.html # Add new location form
    ├── edit_location.html# Edit location form
    ├── movements.html    # Movement history with pagination
    ├── add_movement.html # Add new movement form
    └── balance.html      # Current inventory balance report
Sample Data
The application automatically creates sample data on first run:

Products:

LAPTOP001: Dell Laptop
MOUSE001: Wireless Mouse
KEYBOARD001: Mechanical Keyboard
MONITOR001: 24-inch Monitor
Locations:

WAREHOUSE: Main Warehouse
STOREFRONT: Store Front
STORAGE: Storage Room
SHIPPING: Shipping Dock
Sample Movements:

Initial stock additions to warehouse
Transfers between locations
Sales from storefront
Key Features Implementation
Movement Types
Incoming Stock: from_location is NULL, to_location specified
Outgoing Stock: from_location specified, to_location is NULL
Transfer: Both from_location and to_location specified
Balance Calculation
The balance report calculates current stock by:

Summing all incoming movements (to_location) for each product-location pair
Subtracting all outgoing movements (from_location) for each product-location pair
Displaying only positive balances (locations with actual stock)
Form Validation
Unique constraints on product_id and location_id
Required field validation
Movement logic validation (prevents invalid movement combinations)
Positive quantity validation
Professional UI/UX
Responsive Bootstrap design
Clear navigation and breadcrumbs
Flash messages for user feedback
Professional color scheme and typography
Print-friendly balance reports
Usage Examples
Adding New Stock
Go to Movements → Add New Movement
Select a product
Leave "From Location" empty
Select destination location
Enter quantity
Recording Sales
Go to Movements → Add New Movement
Select a product
Select source location (where product is currently)
Leave "To Location" empty
Enter quantity sold
Transferring Between Locations
Go to Movements → Add New Movement
Select a product
Select source location
Select destination location
Enter quantity to transfer
Testing the Application
Dashboard: View system statistics and recent movements
Add Products: Create new products with unique IDs
Add Locations: Create warehouse/storage locations
Record Movements: Test all three movement types
View Balance: Check current inventory across locations
Edit Functionality: Modify existing products and locations
Technical Implementation Details
Flask Framework: Web application framework
SQLAlchemy ORM: Database operations and relationships
Flask-WTF: Form handling and CSRF protection
Bootstrap 5: Responsive UI framework
Font Awesome: Professional icons
SQLite: Lightweight database (easily replaceable with PostgreSQL/MySQL)
This implementation demonstrates professional Flask development practices including proper project structure, database design, form handling, template inheritance, and user experience design. "# Inventory-Management"
