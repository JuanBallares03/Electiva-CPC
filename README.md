# FastRouteCO

## Introduction

FastRouteCO is an intelligent B2B multi-stop assignment and routing 
system for Colombian companies with their own fleet, with dynamic 
optimization for delivery and pickup routes based on the driver's 
starting point, applicable to any economic sector.

Unlike platforms such as Rappi or DidiFood, which connect businesses 
with independent couriers, FastRouteCO is an internal tool that 
companies use to manage and optimize their own employed drivers 
intelligently and automatically.

## Problem Statement

Colombian companies with their own fleet manage their delivery and 
pickup routes manually. In many cases, orders are assigned via 
WhatsApp or phone calls, while the driver independently decides 
the order of stops. Additionally, the person in charge of operations 
has no real-time information about driver locations and no tools 
to optimize routes.

This situation can lead to higher fuel costs, longer delivery times, 
unnecessary travel and limited visibility over the company's operations.

# System Roles

## 1. Platform Administrator

Responsible for managing FastRouteCO as a platform and for managing 
the companies that use the service.

### Main Functions

- Register and manage companies using FastRouteCO.
- Create and manage administrators for each company.
- Activate or deactivate companies.
- Manage the plans available on the platform.
- View general information about companies.
- Manage general system settings.

## 2. Company Administrator

Responsible for managing a company's account within FastRouteCO 
and viewing general information about its operations.

### Main Functions

- View and manage company information.
- View the contracted plan.
- View subscription status.
- View the limits and features included in the plan.
- Manage the company's administrative users.
- View logistics reports and indicators.
- View general operation statistics.
- View platform usage information.
- Manage general company settings.

## 3. Logistics Supervisor

Responsible for managing and supervising the company's daily 
logistics operations within FastRouteCO.

### Main Functions

- Register and manage drivers.
- Register orders and delivery or pickup points.
- Create and manage routes.
- Assign orders to drivers.
- Execute route optimization.
- Make changes or reassignments to routes when necessary.
- View driver locations in real time.
- Monitor route status.
- View delivery and pickup completion status.
- Manage incidents during routes.
- View driver routes on the map.

## 4. Driver

The user responsible for completing the deliveries or pickups 
assigned by the logistics supervisor.

### Main Functions

- Log in from the mobile application.
- View the assigned route.
- View the stops to be completed.
- View the information for each order.
- Share location via GPS.
- Start and end the route.
- Mark a delivery or pickup as completed.
- Allow stop verification via geofencing.
- Report incidents during the route.
- View the status of the assigned route.

# Role Summary

| Role | Main Responsibility |
|---|---|
| **Platform Administrator** | General management of FastRouteCO and company administration |
| **Company Administrator** | Management of company account, subscription, users and reports |
| **Logistics Supervisor** | Management of drivers, orders, routes and logistics operations |
| **Driver** | Execution of routes and completion of deliveries or pickups |

## Structured prompt

Act as a senior requirements analyst.

Context: B2B web and mobile platform called FastRoute CO for Colombian 
companies with their own driver fleet. The system intelligently assigns 
orders and optimizes multi-stop delivery and pickup routes using AI 
from the driver's real-time starting point. Applicable to any economic 
sector — restaurants, pharmacies, courier services, schools, medical 
delivery, and more. No online payments for now.

Key facts confirmed in real interview with business owner:
- Orders arrive via WhatsApp, phone calls and in-person
- Administrators currently assign orders manually with no visibility 
  of driver location
- Drivers decide their own stop order with no optimization
- No performance records per driver exist
- Drivers are non-technical users (must be simple to use)
- System must work in basic offline mode and sync when reconnected
- Photo evidence required to confirm deliveries
- Business plans to scale to multiple branches in the future

Actors: System Administrator, Client Company, Company Administrator, 
Route Supervisor, Driver, Google Maps API (external)

Modules: role-based login, company and driver management, order and 
pickup point registration, AI multi-stop route optimization (VRP), 
real-time GPS tracking, geofencing stop confirmation, dynamic 
reassignment, logistics reports (basic and advanced), driver-supervisor 
communication, school transport module, subscription plan management

Subscription plans:
- Free Trial: limited time access, up to 2-3 drivers
- Pro: up to 5-10 drivers, basic reports, 1 branch, chat/email support
- Premium: unlimited drivers, advanced reports, multiple branches, 
  dedicated support, school module included

Platforms: web panel for administrators and supervisors, 
mobile app for drivers (Android and iOS)

Tech stack: Node.js / Express backend, Google Maps API or 
OpenStreetMap, low-cost cloud hosting

Task: generate 15 functional requirements prioritized with MoSCoW.

Format: markdown table: ID | Priority | Requirement. End with up to 
3 questions whose answers would change the design.

Constraints: each requirement verifies a single capability; no online 
payments, push notifications or chat; mark with [ASSUMED] anything 
the business has not confirmed.


## Functional Requirements

| ID | Requirement |
|---|---|
| RF01 | Register the routes that need to be optimized |
| RF02 | Register and manage client companies in the system |
| RF03 | Register and manage the drivers of each company's fleet |
| RF04 | Register orders or pickup points with their address and priority |
| RF05 | Automatically assign orders to the most optimal driver based on availability and location |
| RF06 | Dynamically optimize the multi-stop route for each driver from their starting point |
| RF07 | Reassign orders or routes in real time when incidents or cancellations occur |
| RF08 | Display the real-time status and location of each driver on the map |
| RF09 | Notify the driver of their assigned route with the stop order through the mobile app |
| RF10 | Confirm completed delivery or pickup by the driver |
| RF11 | Generate operational efficiency reports by route, driver and company |
| RF12 | Manage the school transport module with student pickup points |
| RF13 | Obtain and update the driver's geographic location in real time via GPS integrated in the mobile app |
| RF14 | Automatically verify and record stop completion using the driver's GPS location upon arrival at the delivery or pickup point (geofencing) |
| RF15 | Integrate the system with an external mapping and geolocation service (such as Google Maps API or OpenStreetMap) to obtain coordinates, calculate distances, trace routes and support real-time GPS tracking |
| RF16 | Allow drivers to upload photographic evidence when confirming a completed delivery or pickup |
| RF17 | Enable basic offline mode on the driver's mobile app, synchronizing data automatically when internet connection is restored |

## Non-Functional Requirements

| ID | Requirement |
|---|---|
| RNF01 | The system must calculate and generate the optimized route in a maximum of 10 seconds |
| RNF02 | The system must update each driver's GPS location in real time with a maximum interval of 5 seconds |
| RNF03 | The system must be available 99% of the time during client companies' operational hours |
| RNF04 | The system must authenticate all users ensuring each actor only accesses the functions corresponding to their role |
| RNF05 | The driver's mobile app must be compatible with Android and iOS devices |
| RNF06 | The system must be scalable to support growth in the number of companies, drivers and orders without degrading performance |
| RNF07 | The system must maintain basic offline functionality when the external geolocation service is unavailable, synchronizing data upon connection recovery |