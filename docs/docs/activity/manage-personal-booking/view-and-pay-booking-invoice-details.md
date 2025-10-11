# Activity View and Pay Booking Invoice Details

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Select function View Invoice Details;

repeat
  :(2) Select booking to view invoice;

  |S|
  :(3) Verify booking status;

  if (Verify booking exists?) then (No)
    :(3.1) Display booking not found error;
    |C|
  else (Yes)
    |S|
    :(4) Display invoice details;
    note right
      - Invoice ID
      - Booking ID
      - Total amount
      - Payment status
      - Payment method
      - Booking details
      - Trip information
    end note

    |C|
    :(5) Select action;

    if (Check action type?) then (Pay Invoice)
      if (Check payment status?) then (Already Paid)
        |S|
        :(5.1) Display already paid notification;
        |C|
      else (Unpaid)
        |C|
        :(6) Select payment method;
        note right
          - Credit/Debit Card
          - Bank Transfer
          - E-Wallet
        end note

        repeat
          :(7) Enter payment information;
          :(8) Submit payment;

          |S|
          :(9) Verify payment information;
          if (Verify payment valid?) then (No)
            :(9.1) Display payment validation error;
          else (Yes)
          endif
        repeat while (Verify payment valid?) is (No) not (Yes)

        :(10) Verify payment processing;
        if (Check payment successful?) then (No)
          :(10.1) Display payment failed notification;
          |C|
        else (Yes)
          |S|
          :(11) Update invoice payment status;
          note right
            - Update payment_status to PAID
            - Update payment_method
            - Update booking status to CONFIRMED
          end note
          :(12) Display payment success notification;
          :(13) Notify payment confirmation via email;
          note right
            - Payment receipt
            - Booking confirmation
            - Trip details
          end note

          |C|
          :(14) Confirm notification;
        endif
      endif
    else (View Only)
      |C|
      :(15) Confirm view;
    endif
  endif
repeat while (Check want to view another invoice?) is (Yes) not (No)

:(16) Confirm end of use case;

stop

@enduml
```

<!-- diagram id="activity-manage-personal-booking-view-and-pay-booking-invoice-details" -->
