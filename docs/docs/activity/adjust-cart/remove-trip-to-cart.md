# Activity Remove Trip from Cart

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function View Cart;

repeat
  :(2) Select cart item;

  |S|
  :(3) Verify cart item status;

  if (Check cart item exists?) then (No)
    :(3.1) Display error notification;
    |C|
  else (Yes)
    |S|
    :(4) Display confirmation dialog;

    |C|
    :(5) Click button;

    if (Check confirmation?) then (Cancel)
      |C|
    else (Confirm)
      |S|
      :(6) Verify cart item data;
      if (Check can remove?) then (No)
        :(6.1) Display error notification;
        |C|
      else (Yes)
        |S|
        :(7) Update cart data;
        note right
          - Delete cart item record
        end note
        :(8) Display success notification;

        |C|
        :(9) Confirm notification;
      endif
    endif
  endif
repeat while (Check want to remove another item?) is (Yes) not (No)

:(10) Confirm end;

stop

@enduml
```

<!-- diagram id="activity-adjust-cart-remove-trip-to-cart" -->
