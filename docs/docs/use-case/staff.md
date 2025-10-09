# Use Case Staff

```plantuml
@startuml
left to right direction
actor Staff

rectangle "Tourist Management System" {
  usecase UC01 as "View Routes"
  usecase UC02 as "View and Filter Routes"
  usecase UC03 as "View Route Detail"

  usecase UC04 as "View Route Schedule"

  usecase UC05 as "View Attraction"
  usecase UC06 as "View and Filter Attractions"
  usecase UC07 as "View Attraction Detail"

  usecase UC08 as "View Trips"
  usecase UC09 as "View and Filter Trips"
  usecase UC10 as "View Trip Detail"
  usecase UC11 as "Add New Booking for Trip"

  usecase UC12 as "Adjust and Track Bookings"
  usecase UC13 as "View and Filter Bookings"
  usecase UC14 as "Add New Booking"
  usecase UC15 as "View Booking Detail"
  usecase UC16 as "Edit Pre-Departure Booking"
  usecase UC17 as "Delete Booking"
  usecase UC18 as "View Booking Invoice"

  usecase UC19 as "Adjust Customers"
  usecase UC20 as "View and Filter Customers"
  usecase UC21 as "Add New Customer"
  usecase UC22 as "View Customer Details"
  usecase UC23 as "Edit Customer"
  usecase UC24 as "Delete Customer"
}

Staff -- UC01
Staff -- UC04
Staff -- UC05
Staff -- UC08
Staff -- UC12
Staff -- UC19

UC01 <.. UC02 : <<extend>>
UC01 <.. UC03 : <<extend>>
UC03 ..> UC02 : <<include>>

UC05 <.. UC06 : <<extend>>
UC05 <.. UC07 : <<extend>>
UC07 ..> UC06 : <<include>>

UC08 <.. UC09 : <<extend>>
UC08 <.. UC10 : <<extend>>
UC08 <.. UC11 : <<extend>>
UC10 ..> UC09 : <<include>>
UC11 ..> UC09 : <<include>>

UC12 <.. UC13 : <<extend>>
UC12 <.. UC14 : <<extend>>
UC12 <.. UC15 : <<extend>>
UC12 <.. UC16 : <<extend>>
UC12 <.. UC17 : <<extend>>
UC12 <.. UC18 : <<extend>>
UC14 ..> UC13 : <<include>>
UC15 ..> UC13 : <<include>>
UC16 ..> UC13 : <<include>>
UC17 ..> UC13 : <<include>>
UC18 ..> UC13 : <<include>>

UC19 <.. UC20 : <<extend>>
UC19 <.. UC21 : <<extend>>
UC19 <.. UC22 : <<extend>>
UC19 <.. UC23 : <<extend>>
UC19 <.. UC24 : <<extend>>
UC21 ..> UC20 : <<include>>
UC22 ..> UC20 : <<include>>
UC23 ..> UC20 : <<include>>
UC24 ..> UC20 : <<include>>

@enduml
```

<!-- diagram id="use-case-staff" -->
