# Activity View and Filter Trips in Cart

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function View Cart;

|S|
:(2) Display cart items;

repeat
  |C|
  :(3) Enter search criteria;
  note right
    - Trip name
    - Date range
    - Price range
  end note
  :(4) Submit search;

  |S|
  :(5) Verify search criteria;

  if (Check has results?) then (No)
    :(5.1) Display no results notification;
    |C|
  else (Yes)
    |S|
    :(6) Display search results;
    note right
      **Extended actions:**
      - Edit Trip Details
      - Remove Trip from Cart
    end note

    |C|
  endif
repeat while (Check want to search again?) is (Yes) not (No)

:(7) Confirm end;

stop

@enduml
```

<!-- diagram id="activity-adjust-cart-view-and-filter-trips-in-cart" -->
