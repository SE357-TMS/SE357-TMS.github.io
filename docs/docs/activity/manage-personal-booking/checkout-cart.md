# Activity Checkout Cart

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function Checkout Cart;

|S|
:(2) Verify cart status;

if (Check cart has items?) then (No)
  :(2.1) Display empty cart notification;
  |C|
else (Yes)
  |S|
  :(3) Display cart items;

  |C|
  :(4) Select cart items to checkout;

  |S|
  :(5) Display checkout form;
  note right
    - Selected items summary
    - Total amount
    - Contact information
    - Passenger details for each trip
  end note

  repeat
    |C|
    :(6) Enter checkout information;
    :(7) Submit checkout information;

    |S|
    :(8) Verify checkout information;
    if (Check data valid?) then (No)
      :(8.1) Display validation error;
    else (Yes)
    endif
  repeat while (Check data valid?) is (No) not (Yes)

  :(9) Verify selected trips availability;
  if (Check all selected trips available?) then (No)
    :(9.1) Display unavailable trips notification;
    |C|
  else (Yes)
    |S|
    :(10) Update booking data;
    note right
      - Create tour bookings for selected items
      - Create booking details
      - Create booking travelers
      - Update trips booked seats
      - Create invoices
      - Remove selected cart items
    end note
    :(11) Display success notification;
    :(12) Notify booking confirmation;
    note right
      - Send email with booking IDs
      - Payment deadline
      - Booking details
      - Payment instructions
    end note

    |C|
    :(13) Confirm notification;
  endif
endif

:(14) Confirm end;

stop

@enduml
```

<!-- diagram id="activity-manage-personal-booking-checkout-cart" -->
