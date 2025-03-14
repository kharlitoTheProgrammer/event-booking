<template>
  <main class="container mx-auto my-8 space-y-8">
    <h1 class="text-4xl font-medium">Event Booking App</h1>

    <h2 class="text-2xl font-medium">All Events</h2>

    <div class="grid grid-cols-2 gap-8">
      <EventCard
        v-for="i in 8"
        :key="i"
        title="Vue Conference"
        when="3-11-2025"
        description="Vue conference where we'll talk about JavaScript and Vue"
        @register="console.log('Registered!')"
      />
    </div>

    <h2 class="text-2xl font-medium">Your Bookings</h2>
    <section class="grid grid-cols-1 gap-8">
      <BookingItem v-for="i in 3" :key="i" />
    </section>
  </main>
</template>

<script setup lang="ts">
import EventCard from "@/components/EventCard.vue";
import BookingItem from "./components/BookingItem.vue";
</script>
