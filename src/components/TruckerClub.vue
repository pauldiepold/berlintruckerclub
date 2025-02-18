<script setup lang="ts">
import { ref } from 'vue';

const membershipTiers = ref([
  {
    level: 'BRONZE STATUS',
    requirement: 'Mind. 80 km/h auf der Autobahn',
    subtext: '(mit voller Ladung)'
  },
  {
    level: 'SILBER STATUS',
    requirement: 'Mind. 90 km/h auf der Autobahn',
    subtext: '(auch bei Gegenwind)'
  },
  {
    level: 'GOLD STATUS',
    requirement: 'Mind. 100 km/h auf der Autobahn',
    subtext: '(ohne Tempolimit-Anzeige)'
  }
]);

const philosophyQuotes = ref([
  'Wir sind eine Gemeinschaft von leidenschaftlichen Truckern, die das Tempo lieben. Unsere Mission ist es, die schnellsten und stylischsten Trucker Berlins zu vereinen.',
  'Bei uns gibt es keine Ausreden – nur Diesel und Determination.',
  'Jeder Kilometer zählt, aber nur wenn er schnell genug war.'
]);

const events = ref([
  {
    title: 'Autobahn Sprint Challenge',
    schedule: 'Jeden ersten Montag im Monat, 3:00 Uhr',
    location: 'Treffpunkt: Raststätte Grunewald',
    requirement: '*Teilnahme nur mit gültigem Führerschein und mindestens 40-Tonner'
  }
]);

const navItems = ref([
  { text: 'Home', href: '/' },
  { text: 'Mitgliedschaft', href: '/mitgliedschaft' },
  { text: 'Events', href: '/events' }
]);
</script>

<template>
  <div class="relative min-h-screen">
    <!-- Background image with overlay -->
    <div class="fixed inset-0 z-0">
      <img src="@/assets/truck.png" alt="Background" class="w-full h-full object-cover"/>
      <div class="absolute inset-0 bg-black/60"></div>
    </div>

    <!-- Content wrapper -->
    <div class="relative z-10 text-white">
      <!-- Navigation -->
      <nav class="bg-black/40 backdrop-blur-sm">
        <div class="container mx-auto flex justify-between items-center p-4">
          <h1 class="text-2xl font-bold">BERLIN TRUCKER CLUB</h1>
          <div class="space-x-4">
            <a v-for="item in navItems"
               :key="item.text"
               :href="item.href"
               class="hover:text-gray-300 transition duration-300">
              {{ item.text }}
            </a>
          </div>
        </div>
      </nav>

      <main class="container mx-auto mt-16 px-4">
        <!-- Hero Section -->
        <div class="text-center py-20">
          <h2 class="text-6xl font-bold mb-4">BERLIN TRUCKER CLUB</h2>
          <p class="text-2xl">Weil echte Ausdauer sich in Kilometern pro Stunde misst</p>
        </div>

        <!-- Membership Tiers -->
        <section class="my-16">
          <h2 class="text-3xl font-bold mb-8 text-center">UNSERE AUFNAHMEKRITERIEN</h2>
          <div class="grid md:grid-cols-3 gap-8">
            <div v-for="tier in membershipTiers"
                 :key="tier.level"
                 class="bg-white/10 backdrop-blur-md p-6 rounded-lg border border-white/20 hover:bg-white/20 transition duration-300">
              <h3 class="text-xl font-bold mb-4">{{ tier.level }}</h3>
              <p>
                {{ tier.requirement }}<br>
                <span class="text-gray-300">{{ tier.subtext }}</span>
              </p>
            </div>
          </div>
        </section>

        <!-- Philosophy -->
        <section class="my-16">
          <h2 class="text-3xl font-bold mb-8 text-center">CLUB PHILOSOPHIE</h2>
          <div class="bg-white/10 backdrop-blur-md p-8 rounded-lg border border-white/20">
            <p v-for="(quote, index) in philosophyQuotes"
               :key="index"
               class="text-xl mb-4 last:mb-0 italic">
              "{{ quote }}"
            </p>
          </div>
        </section>

        <!-- Events -->
        <section class="my-16">
          <h2 class="text-3xl font-bold mb-8 text-center">NÄCHSTE EVENTS</h2>
          <div v-for="event in events"
               :key="event.title"
               class="bg-white/10 backdrop-blur-md p-6 rounded-lg border border-white/20 hover:bg-white/20 transition duration-300">
            <h3 class="text-xl font-bold mb-4">{{ event.title }}</h3>
            <p class="mb-4">
              {{ event.schedule }}<br>
              {{ event.location }}
            </p>
            <p class="italic text-gray-300">{{ event.requirement }}</p>
          </div>
        </section>
      </main>

      <!-- Footer -->
      <footer class="bg-black/40 backdrop-blur-sm py-8 mt-16">
        <div class="container mx-auto px-4 text-center">
          <p>© 2025 Berlin Trucker Club</p>
          <p class="mt-2">Fastest Truckers in Town</p>
        </div>
      </footer>
    </div>
  </div>
</template>

<style>
/* Falls zusätzliche Stile benötigt werden */
</style>
