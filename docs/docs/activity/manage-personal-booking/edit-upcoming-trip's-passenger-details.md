# Activity Edit Upcoming Trip's Passenger Details

```plantuml
@startuml
|C|Customer
|S|System
|D|Database

|C|
start
:(1) Select booking to edit;
|S|
:(2) Get booking details;
|D|
:(3) Query booking data;
if () then (Booking not found)
  |S|
  :(3.1) Display error notification;
  stop
elseif () then (Trip already started)
  |S|
  :(3.2) Display error notification;
  stop
elseif () then (Booking canceled)
  |S|
  :(3.3) Display error notification;
  stop
else (Valid)
  |S|
  :(4) Display passenger details;
  repeat
    |C|
    :(5) Enter new passenger details;
    note right
      - Full name
      - Date of birth
      - Gender
      - Nationality
      - Identity document
    end note
    |S|
    :(6) Validate input data;
  backward: (6.1) Display error notification;
  repeat while () is (Invalid data) not (Valid data)
  |C|
  :(6.2) Click "Save" button to confirm;
  |S|
  :(7) Process update request;
  |D|
  :(8) Validate data;
  if () then (Invalid data)
    |S|
    :(8.1) Display error notification;
  else (Valid data)
    |D|
    :(8.2) Update booking traveler records;
    |S|
    :(9) Display success notification;
    :(10) Send update confirmation;
  endif
endif
stop

@enduml
```

<!-- diagram id="activity-manage-personal-booking-edit-upcoming-trip's-passenger-details" -->
