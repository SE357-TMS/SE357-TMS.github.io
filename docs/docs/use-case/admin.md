# Use Case Admin

```plantuml
@startuml
left to right direction
actor Admin

rectangle "Tourist Management System" {

  usecase UC01 as "Manage Routes"
  usecase UC02 as "View and Filter Routes"
  usecase UC03 as "Add Route"
  usecase UC04 as "View Route Detail"
  usecase UC05 as "Edit Route Detail"
  usecase UC06 as "Delete Route"

  usecase UC07 as "Manage Route Schedule"
  usecase UC08 as "View Route Schedule"
  usecase UC09 as "Add Itinerary"
  usecase UC10 as "Edit Itinerary"
  usecase UC11 as "Delete Itinerary"

  usecase UC12 as "Manage Attraction"
  usecase UC17 as "View and Filter Attractions"
  usecase UC13 as "Add Attraction"
  usecase UC14 as "View Attraction Detail"
  usecase UC15 as "Edit Attraction Detail"
  usecase UC16 as "Delete Attraction"




  usecase UC18 as "Manage Trips"
  usecase UC19 as "View and Filter Trips"
  usecase UC20 as "Add Trip"
  usecase UC21 as "View Trip Detail"
  usecase UC22 as "Edit Trip"
  usecase UC23 as "Add Booking for Trip"
  usecase UC24 as "Delete Trip"


  usecase UC25 as "Adjust Customers"
  usecase UC26 as "View and Filter Customers"
  usecase UC27 as "Add Customer "
  usecase UC28 as "View Customer Detail"
  usecase UC29 as "Edit Customer"
  usecase UC30 as "Delete Customer"

  usecase UC31 as "Adjust Staffs"
  usecase UC32 as "View and Filter Staffs"
  usecase UC33 as "Add Staff"
  usecase UC34 as "View Staff Detail"
  usecase UC35 as "Edit Staff"
  usecase UC36 as "Delete Staff"

  usecase UC37 as "View Reports"
}


Admin -- UC01
Admin -- UC07
Admin -- UC12
Admin -- UC18

Admin -- UC25
Admin -- UC31
Admin -- UC37


UC01 <.. UC02 : <<extend>>
UC01 <.. UC03 : <<extend>>
UC01 <.. UC04 : <<extend>>
UC01 <.. UC05 : <<extend>>
UC01 <.. UC06 : <<extend>>
UC03 ..> UC02 : <<include>>
UC04 ..> UC02 : <<include>>
UC05 ..> UC02 : <<include>>
UC06 ..> UC02 : <<include>>

UC07 <.. UC08 : <<extend>>
UC07 <.. UC09 : <<extend>>
UC07 <.. UC10 : <<extend>>
UC07 <.. UC11 : <<extend>>

UC12 <.. UC13 : <<extend>>
UC12 <.. UC14 : <<extend>>
UC12 <.. UC15 : <<extend>>
UC12 <.. UC16 : <<extend>>
UC12 <.. UC17 : <<extend>>
UC13 ..> UC17 : <<include>>
UC14 ..> UC17 : <<include>>
UC15 ..> UC17 : <<include>>
UC16 ..> UC17 : <<include>>

UC18 <.. UC19 : <<extend>>
UC18 <.. UC20 : <<extend>>
UC18 <.. UC21 : <<extend>>
UC18 <.. UC22 : <<extend>>
UC18 <.. UC23 : <<extend>>
UC18 <.. UC24 : <<extend>>
UC20 ..> UC19 : <<include>>
UC21 ..> UC19 : <<include>>
UC22 ..> UC19 : <<include>>
UC23 ..> UC19 : <<include>>
UC24 ..> UC19 : <<include>>


UC25 <.. UC26 : <<extend>>
UC25 <.. UC27 : <<extend>>
UC25 <.. UC28 : <<extend>>
UC25 <.. UC29 : <<extend>>
UC25 <.. UC30 : <<extend>>
UC27 ..> UC26 : <<include>>
UC28 ..> UC26 : <<include>>
UC29 ..> UC26 : <<include>>
UC30 ..> UC26 : <<include>>

UC31 <.. UC32 : <<extend>>
UC31 <.. UC33 : <<extend>>
UC31 <.. UC34 : <<extend>>
UC31 <.. UC35 : <<extend>>
UC31 <.. UC36 : <<extend>>
UC33 ..> UC32 : <<include>>
UC34 ..> UC32 : <<include>>
UC35 ..> UC32 : <<include>>
UC36 ..> UC32 : <<include>>

@enduml
```

<!-- diagram id="use-case-admin" -->
