# Activity View and Filter Personal Bookings

```plantuml
@startuml
|C|Customer
|S|System
|D|Database

|S|
start
:(1) Display personal bookings view;

|C|
:(2) Choose options;
if () then (Book a Trip)
  :(2.1) Activity Book a Trip;
elseif () then (Edit Passenger Details)
  :(2.2) Activity Edit Upcoming Trip's Passenger Details;
elseif () then (Filter Bookings)
  |C|
  :(2.3) Select filter criteria;
  note right
    - Status (PENDING, CONFIRMED,
      CANCELED, COMPLETED)
    - Date range
    - Destination
  end note
  |S|
  :(2.4) Process filter request;
  |D|
  :(2.5) Query bookings by filters;
  |S|
  :(2.6) Display filtered results;
else (View Invoice Details)
  :(2.7) Activity View and Pay Booking Invoice Details;
endif

stop
@enduml
```

<!-- diagram id="activity-manage-personal-booking-view-and-filter-personal-bookings" -->
