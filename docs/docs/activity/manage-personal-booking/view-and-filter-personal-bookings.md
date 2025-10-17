# Activity View and Filter Personal Bookings

```plantuml
@startuml
|C|Customer
|S|System

|C|
start

:(1) Click my bookings in menu;

|S|
:(2) Query booking list from database;

if (Check customer has bookings?) then (No)
  :(2.1) Display no bookings message with explore tours button;

  |C|
  :(2.2) Confirm end;

  stop
else (Yes)
endif

|S|
:(3) Display bookings with three tabs;

:(4) Display each booking with details and action buttons;

|C|
:(5) View booking list;

repeat
  if (Check want to filter?) then (Yes)
    :(6) Click filter and select criteria;

    |S|
    :(7) Display filter form;

    |C|
    :(8) Enter filter criteria;

    :(9) Click apply button;

    |S|
    :(10) Query bookings with filter conditions;

    if (Check has matching results?) then (No)
      :(10.1) Display no matching bookings message;
    else (Yes)
      :(11) Display filtered booking list;
    endif

    |C|
  else (No)
  endif
repeat while (Check want to continue filtering?) is (Yes) not (No)

:(12) Confirm end;

stop

@enduml
```

<!-- diagram id="activity-manage-personal-booking-view-and-filter-personal-bookings" -->
