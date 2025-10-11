# Activity View and Filter Available Trips

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function Browse Trips;

|S|
:(2) Display available trips view;
note right
  - All scheduled trips
  - Trip information
  - Available seats
  - Price
end note

repeat
  |C|
  :(3) Select action;

  if (Check action type?) then (Filter Trips)
    :(4) Select filter criteria;
    note right
      - Destination
      - Date range
      - Price range
      - Available seats
      - Route status
    end note
    :(5) Submit filter;

    |S|
    :(6) Verify filter criteria;
    if (Verify criteria valid?) then (No)
      :(6.1) Display filter validation error;
      |C|
    else (Yes)
      :(7) Display filtered trip results;
      note right
        - Matching trips
        - Trip details
        - Available seats
        - Price
      end note

      |C|
    endif
  else (Check action type?)
    if (Check action type?) then (View Trip Details)
      :(8) Select trip;

      |S|
      :(9) Verify trip availability;
      if (Verify trip exists?) then (No)
        :(9.1) Display trip not found error;
        |C|
      else (Yes)
        :(10) Display trip details view;
        note right
          Activity: View Trip Details
        end note

        |C|
      endif
    else (Reset Filter)
      |S|
      :(11) Display all available trips;

      |C|
    endif
  endif

  |C|
repeat while (Check want to continue browsing?) is (Yes) not (No)

:(12) Confirm end of use case;

stop

@enduml
```

<!-- diagram id="activity-browse-trips-view-and-filter-available-trips" -->
