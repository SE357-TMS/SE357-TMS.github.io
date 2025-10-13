# Activity Edit Upcoming Trip's Passenger Details

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function Edit Passenger Details;

repeat
  :(2) Select booking;

  |S|
  :(3) Verify booking status;

  if (Check booking valid and editable?) then (No)
    :(3.1) Display error notification;
    |C|
  else (Yes)
    |S|
    :(4) Display passenger details form;
    note right
      - Full name
      - Date of birth
      - Gender
      - Nationality
      - Identity document
    end note

    repeat
      |C|
      :(5) Enter passenger details;
      :(6) Submit changes;

      |S|
      :(7) Verify input data;
      if (Check data valid?) then (No)
        :(7.1) Display validation error;
      else (Yes)
      endif
    repeat while (Check data valid?) is (No) not (Yes)

    :(8) Update passenger information;
    note right
      - Update booking traveler records
    end note
    :(9) Display success notification;
    :(10) Notify update confirmation;

    |C|
    :(11) Confirm notification;
  endif
repeat while (Check want to edit another booking?) is (Yes) not (No)

:(12) Confirm end;

stop

@enduml
```

<!-- diagram id="activity-manage-personal-booking-edit-upcoming-trip's-passenger-details" -->
