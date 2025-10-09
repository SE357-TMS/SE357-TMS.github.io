# Use Case Customer

```plantuml
@startuml
left to right direction
actor Customer

rectangle "Tourist Management System" {
  usecase UC01 as "Manage Personal Bookings"
  usecase UC02 as "Book a Trip"
  usecase UC03 as "Edit Upcoming Trip's\nPassenger Details"
  usecase UC04 as "View and Filter\nPersonal Bookings"
  usecase UC05 as "View and Pay\nBooking Invoice Details"

  usecase UC06 as "Browse Trips"
  usecase UC07 as "View and Filter\nAvailable Trips"
  usecase UC08 as "View Trip Details"

  usecase UC09 as "Adjust Cart"
  usecase UC10 as "Add Trip to Cart"
  usecase UC11 as "Remove Trip from Cart"
  usecase UC12 as "Edit Cart Details"
  usecase UC13 as "View and Filter\nTrips in Cart"

  usecase UC14 as "Adjust Favorite Trips"
  usecase UC15 as "Favorite a Trip"
  usecase UC16 as "Unfavorite a Trip"
  usecase UC17 as "View and Filter\nFavorite Trips"
}

Customer -- UC01
Customer -- UC06
Customer -- UC09
Customer -- UC14

UC01 <.. UC02 : <<extend>>
UC01 <.. UC03 : <<extend>>
UC01 <.. UC04 : <<extend>>
UC01 <.. UC05 : <<extend>>
UC02 ..> UC07 : <<include>>
UC03 ..> UC04 : <<include>>

UC06 <.. UC07 : <<extend>>
UC06 <.. UC08 : <<extend>>
UC08 ..> UC07 : <<include>>

UC09 <.. UC10 : <<extend>>
UC09 <.. UC11 : <<extend>>
UC09 <.. UC12 : <<extend>>
UC09 <.. UC13 : <<extend>>
UC10 ..> UC07 : <<include>>
UC12 ..> UC13 : <<include>>

UC14 <.. UC15 : <<extend>>
UC14 <.. UC16 : <<extend>>
UC14 <.. UC17 : <<extend>>
UC15 ..> UC07 : <<include>>
UC16 ..> UC17 : <<include>>

@enduml
```

<!-- diagram id="use-case-customer" -->
