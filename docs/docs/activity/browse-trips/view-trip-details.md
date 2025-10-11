# Activity View Trip Details

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function View Trip Details;

repeat
  :(2) Select trip to view;

  |S|
  :(3) Verify trip status;

  if (Verify trip exists?) then (No)
    :(3.1) Display trip not found error;
    |C|
  else (Yes)
    |S|
    :(4) Display trip details;
    note right
      - Trip ID
      - Route information
      - Departure/Return dates
      - Price
      - Total/Available seats
      - Pick-up time & location
      - Status
      - Route attractions by day
      - Duration
    end note

    |C|
    :(5) Select action;

    if (Check action type?) then (Book This Trip)
      :(6) Proceed to booking;
      note right
        Activity: Book a Trip
      end note
    else (Check action type?)
      if (Check action type?) then (Add to Favorites)
        |S|
        :(7) Verify favorite status;
        if (Check already in favorites?) then (Yes)
          :(7.1) Display already favorited notification;
          |C|
        else (No)
          |S|
          :(8) Update favorite tours;
          note right
            - Create favorite tour record
          end note
          :(9) Display add to favorites success notification;

          |C|
          :(10) Confirm notification;
        endif
      else (View Only)
        |C|
        :(11) Confirm view;
      endif
    endif
  endif

  |C|
repeat while (Check want to view another trip?) is (Yes) not (No)

:(12) Confirm end of use case;

stop

@enduml
```

<!-- diagram id="activity-browse-trips-view-trip-details" -->
