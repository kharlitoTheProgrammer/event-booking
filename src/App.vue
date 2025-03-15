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
          @register="console.log('Registered!')"
        />
      </template>
      <template v-else>
        <LoadingEventCard v-for="i in 4" :key="i"></LoadingEventCard>
      </template>
    </div>

    <h2 class="text-2xl font-medium">Your Bookings</h2>
    <section class="grid grid-cols-1 gap-8">
      <BookingItem v-for="i in 3" :key="i" />
    </section>
  </main>
</template>

<script setup>
import EventCard from "@/components/EventCard.vue";
import BookingItem from "./components/BookingItem.vue";
import { onMounted, ref } from "vue";
import LoadingEventCard from "./components/LoadingEventCard.vue";

// variable for the events
const events = ref([]);
const eventsLoading = ref(false);

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

// use onMounted
onMounted(() => {
  fetchEvents();
});
</script>
