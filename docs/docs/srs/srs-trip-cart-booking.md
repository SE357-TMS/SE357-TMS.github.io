# 3. Browse Trips

## 3.1 View and Filter Available Trips

### Description

Allows customers to view a list of available trips and apply filters (e.g., destination, date, price, type).

### Functional Requirements

- Display all available trips with key details (destination, date, price, type).
- Provide filter options for destination, date range, price range, and trip type.
- Show filtered results instantly as criteria are selected.
- Allow sorting by price, date, or popularity.
- Support pagination for large result sets.

### Preconditions

- Customer is authenticated (if required for viewing trips).
- Trip data is available in the system.

### Postconditions

- Customer sees a list of trips matching selected filters.

### Activity Diagram

See: `docs/docs/activity/browse-trips/view-and-filter-available-trips.md`

---

## 3.2 View Trip Details

### Description

Allows customers to view detailed information about a selected trip.

### Functional Requirements

- Display trip details: itinerary, price, available dates, included services, cancellation policy, reviews.
- Show images and/or promotional media for the trip.
- Allow customer to view related trips or suggestions.
- Provide option to add trip to cart.

### Preconditions

- Customer has selected a trip from the list.

### Postconditions

- Customer sees all details for the selected trip.

### Activity Diagram

See: `docs/docs/activity/browse-trips/view-trip-details.md`

---

# 4. Adjust Cart

## 4.1 Add Trip to Cart

### Description

Allows customers to add a selected trip to their cart for later booking.

### Functional Requirements

- Add selected trip to cart.
- Validate trip availability before adding.
- Show confirmation message upon successful addition.
- Prevent duplicate entries for the same trip.

### Preconditions

- Customer is authenticated.
- Trip is available for booking.

### Postconditions

- Trip is added to the customer's cart.

### Activity Diagram

See: `docs/docs/activity/manage-cart/add-trip-to-cart.md`

---

## 4.2 Edit Trip Details in Cart

### Description

Allows customers to modify trip details (e.g., number of passengers, options) in their cart.

### Functional Requirements

- Edit number of passengers, selected options, or dates for trips in cart.
- Validate changes (e.g., availability, pricing).
- Update cart totals and details accordingly.

### Preconditions

- Trip is present in the customer's cart.

### Postconditions

- Cart reflects updated trip details.

### Activity Diagram

See: `docs/docs/activity/manage-cart/edit-trip-details.md`

---

## 4.3 Remove Trip from Cart

### Description

Allows customers to remove a trip from their cart.

### Functional Requirements

- Remove selected trip from cart.
- Update cart totals and details.
- Show confirmation message upon successful removal.

### Preconditions

- Trip is present in the customer's cart.

### Postconditions

- Trip is removed from the customer's cart.

### Activity Diagram

See: `docs/docs/activity/manage-cart/remove-trip-to-cart.md`

---

## 4.4 View and Filter Trips in Cart

### Description

Allows customers to view all trips in their cart and apply filters.

### Functional Requirements

- Display all trips currently in cart with key details.
- Provide filter options (e.g., by date, destination).
- Show cart totals and summary.

### Preconditions

- Customer has at least one trip in cart.

### Postconditions

- Customer sees a filtered list of trips in their cart.

### Activity Diagram

See: `docs/docs/activity/manage-cart/view-and-filter-trips-in-cart.md`

---

# 5. Manage Personal Booking

## 5.1 Checkout Cart (Book Trips)

### Description

Allows customers to book all trips in their cart, entering passenger details and making payment.

### Functional Requirements

- Collect passenger details for each trip.
- Validate all required information and trip availability.
- Calculate total price and show invoice.
- Support multiple payment methods.
- Confirm booking and generate booking reference.
- Send confirmation email/SMS.

### Preconditions

- Customer is authenticated.
- Cart contains at least one trip.

### Postconditions

- Trips are booked and booking records created.

### Activity Diagram

See: `docs/docs/activity/manage-cart/checkout-cart.md`

---

## 5.2 View and Filter Personal Bookings

### Description

Allows customers to view and filter their personal bookings.

### Functional Requirements

- Display all bookings made by the customer with key details.
- Provide filter options (e.g., by date, status, destination).
- Show booking status (upcoming, completed, cancelled).

### Preconditions

- Customer has made at least one booking.

### Postconditions

- Customer sees a filtered list of their bookings.

### Activity Diagram

See: `docs/docs/activity/manage-personal-booking/view-and-filter-personal-bookings.md`

---

## 5.3 Edit Upcoming Trip's Passenger Details

### Description

Allows customers to edit passenger details for upcoming trips.

### Functional Requirements

- Edit passenger names, contact info, or special requests for upcoming trips.
- Validate changes and update booking records.
- Restrict edits for trips that are completed or cancelled.

### Preconditions

- Booking is upcoming and editable.

### Postconditions

- Booking reflects updated passenger details.

### Activity Diagram

See: `docs/docs/activity/manage-personal-booking/edit-upcoming-trip's-passenger-details.md`

---

## 5.4 View and Pay Booking Invoice Details

### Description

Allows customers to view invoice details for bookings and make payments if required.

### Functional Requirements

- Display invoice details for each booking (amount, due date, payment status).
- Support payment for unpaid invoices.
- Show payment confirmation and update booking status.

### Preconditions

- Booking has an outstanding invoice.

### Postconditions

- Invoice is paid and booking status updated.

### Activity Diagram

See: `docs/docs/activity/manage-personal-booking/view-and-pay-booking-invoice-details.md`

---

## 5.5 Book a Trip Directly

### Description

Allows customers to book a trip directly from trip details, bypassing the cart.

### Functional Requirements

- Collect passenger details and payment for a single trip.
- Validate all required information and trip availability.
- Confirm booking and generate booking reference.
- Send confirmation email/SMS.

### Preconditions

- Customer is authenticated.
- Trip is available for booking.

### Postconditions

- Trip is booked and booking record created.

### Activity Diagram

See: `docs/docs/activity/manage-personal-booking/book-a-trip.md`

---
