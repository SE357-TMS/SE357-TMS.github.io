# Activity Add Trip to Cart

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select button Add Trip to Cart;

repeat
  :(2) Choose trip details;

  |S|
  :(3) Verify trip status;

  if (Check trip exists and has available seats?) then (No)
    :(3.1) Display error notification;
    |C|
  else (Yes)
    |S|
    :(4) Display quantity form;

    repeat
      |C|
      :(5) Enter quantity;
      :(6) Submit quantity;

      |S|
      :(7) Verify quantity;
      if (Check quantity valid?) then (No)
        :(7.1) Display validation error;
      else (Yes)
      endif
    repeat while (Check quantity valid?) is (No) not (Yes)

    :(8) Verify seat availability;
    if (Check enough seats?) then (No)
      :(8.1) Display insufficient seats notification;
      |C|
    else (Yes)
      |S|
      :(9) Update cart data;
      note right
        - Create/Update cart item
        - Calculate price
      end note
      :(10) Display success notification;

      |C|
      :(11) Confirm notification;
    endif
  endif
repeat while (Check want to add another trip?) is (Yes) not (No)

:(12) Confirm end;

stop

@enduml
```

<!-- diagram id="activity-adjust-cart-add-trip-to-cart" -->
