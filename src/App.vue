<template>
  <main class="container mx-auto my-8 space-y-8">
    <h1 class="text-4xl font-medium">Event Booking App</h1>

    <h2 class="text-2xl font-medium">All Events</h2>

    <div class="grid grid-cols-2 gap-8">
      <template v-if="!eventsLoading">
        <EventCard
          v-for="event in events"
          :key="event.id"
          :title="event.title"
          :when="event.date"
          :description="event.description"
          @register="handleRegistration(event)"
        />
      </template>
      <template v-else>
        <LoadingEventCard v-for="i in 4" :key="i"></LoadingEventCard>
      </template>
    </div>

    <h2 class="text-2xl font-medium">Your Bookings</h2>
    <template v-if="!bookingsLoading">
      <BookingItem
        v-for="booking in bookings"
        :key="booking.id"
        :title="booking.eventTitle"
      ></BookingItem>
    </template>
    <template v-else>
      <LoadingBookingItem v-for="i in 4" :key="i"></LoadingBookingItem>
    </template>
  </main>
</template>

<script setup>
import EventCard from "@/components/EventCard.vue";
import BookingItem from "./components/BookingItem.vue";
import { onMounted, ref } from "vue";
import LoadingEventCard from "./components/LoadingEventCard.vue";
import LoadingBookingItem from "./components/LoadingBookingItem.vue";

// variable for the events
const events = ref([]);
const bookings = ref([]);
const eventsLoading = ref(false);
const bookingsLoading = ref(false);

// fetch events function (use async await)
const fetchEvents = async () => {
  eventsLoading.value = true;
  try {
    const res = await fetch("http://localhost:3001/events");
    events.value = await res.json();
  } finally {
    eventsLoading.value = false;
  }
};

const fetchBookings = async () => {
  bookingsLoading.value = true;
  try {
    const res = await fetch("http://localhost:3001/bookings");
    bookings.value = await res.json();
  } finally {
    bookingsLoading.value = false;
  }
};

const handleRegistration = async (event) => {
  const newBooking = {
    id: Date.now().toString(),
    eventId: event.id,
    eventTitle: event.title,
  };

  await fetch("http://localhost:3001/bookings", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ ...newBooking, status: "confirmed!" }),
  });
};

// use onMounted
onMounted(() => {
  fetchEvents();
  fetchBookings();
});
</script>
