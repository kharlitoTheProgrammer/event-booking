<script setup>
import EventCard from "@/components/EventCard.vue";
</script>

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

    <h2 class="text-2xl font-medium">All Bookings</h2>
  </main>
</template>
