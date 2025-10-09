# Activity Book a Trip

```plantuml
@startuml
|C|Customer
|S|System
|D|Database

|C|
start
:(1) Select trip to book;
|S|
:(2) Get trip details;
|D|
:(3) Query trip data;
if () then (Trip not found)
  |S|
  :(3.1) Display error notification;
  stop
elseif () then (No available seats)
  |S|
  :(3.2) Display error notification;
  stop
else (Valid)
  |S|
  :(4) Display booking form;
  |C|
  :(5) Enter booking information;
  note right
    - Number of passengers
    - Adult count
    - Children count
    - Contact information
    - Passenger details
  end note
  :(6) Submit booking;
  |S|
  :(7) Validate booking information;
  if () then (Invalid input)
    |S|
    :(7.1) Display error notification;
    |C|
    :(7.2) Correct information;
    |S|
    :(7.3) Revalidate;
  else (Valid)
  endif
  |D|
  :(8) Validate seat availability;
  if () then (Insufficient seats)
    |S|
    :(8.1) Display error notification;
    stop
  else (Available)
    :(9) Create tour booking record;
    :(10) Create booking detail record;
    :(11) Create booking traveler records;
    :(12) Update trip booked seats;
    :(13) Create invoice record;
    |S|
    :(14) Display booking success;
    :(15) Send booking confirmation;
    note right
      - Booking ID
      - Payment deadline
      - Booking details
      - Payment instructions
    end note
  endif
endif
stop

@enduml
```

<!-- diagram id="activity-manage-personal-booking-book-a-trip" -->
