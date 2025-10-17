# Activity Edit Route Details

```plantuml
@startuml
|S|Staff
|Sy|System

|S|
start

:(1) Select function Edit Route;

|Sy|
:(2) Verify route exists;

if (Check route exists?) then (No)
  :(2.1) Display route not found error;

  |S|
  :(2.2) Confirm end;
else (Yes)
  |Sy|
  :(3) Verify route status;

  if (Check route not closed?) then (No)
    :(3.1) Display cannot edit closed route error;

    |S|
    :(3.2) Confirm end;
  else (Yes)
    |Sy|
    :(4) Display route edit form;

    repeat
      |S|
      :(5) Edit route information;
      :(6) Edit attractions list;
      :(7) Submit changes;

      |Sy|
      :(8) Verify route information;

      if (Check data valid?) then (No)
        :(8.1) Display validation error;
        |S|
      else (Yes)
        |Sy|
        :(9) Verify route name unique;

        if (Check route name not exists or same?) then (No)
          :(9.1) Display duplicate name error;
          |S|
        else (Yes)
          |Sy|
          :(10) Update route data;

          if (Check database update successful?) then (No)
            :(10.1) Display database error;
            |S|
          else (Yes)
            |Sy|
            :(11) Display success notification;
            |S|
          endif
        endif
      endif
    repeat while (Check data valid and successful?) is (No) not (Yes)

    :(12) Confirm end;
  endif
endif

stop

@enduml
```

<!-- diagram id="activity-manage-routes-edit-route-details" -->
