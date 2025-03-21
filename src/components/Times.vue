<script setup lang="ts">
import { Times } from '../times/types';

defineProps<{ times: Times }>()
</script>

<template>
  <table class="table table-striped table-sm">
    <thead>
      <tr>
        <th scope="col"></th>
        <th scope="col">Time</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Astronomical Dawn</td>
        <td>{{ times.astronomicalDawn }}</td>
      </tr>
      <tr>
        <td>Nautical Dawn</td>
        <td> {{ times.nauticalDawn }}</td>
      </tr>
      <tr>
        <td>Civil Dawn</td>
        <td> {{ times.civilDawn }}</td>
      </tr>
      <tr>
        <td>Sunrise</td>
        <td> {{ times.sunrise }}</td>
      </tr>
      <tr>
        <td>Noon</td>
        <td>{{ times.noon }}</td>
      </tr>
      <tr>
        <td>Sunset</td>
        <td>{{ times.sunset }}</td>
      </tr>
      <tr>
        <td>Civil Dusk</td>
        <td>{{ times.civilDusk }}</td>
      </tr>
      <tr>
        <td>Nautical Dusk</td>
        <td>{{ times.nauticalDusk }}</td>
      </tr>
      <tr>
        <td>Astrological Dusk</td>
        <td>{{ times.astrologicalDusk }}</td>
      </tr>
      <tr>
        <td>Nadir</td>
        <td>{{ times.nadir }}</td>
      </tr>
      <tr>
        <td>&nbsp;</td>
        <td>&nbsp;</td>
      </tr>
      <tr>
        <td>Fajr (15&#176;)</td>
        <td> {{ times.fifteenDawn }}</td>
      </tr>
      <tr>
        <td>Isha (15&#176;)</td>
        <td> {{ times.fifteenDusk }}</td>
      </tr>
      <tr>
        <td>&nbsp;</td>
        <td>&nbsp;</td>
      </tr>
      <tr v-if="times.moonRise">
        <td>Moon Rise</td>
        <td>{{ times.moonRise }}</td>
      </tr>
      <tr v-if="times.moonSet">
        <td>Moon Set</td>
        <td> {{ times.moonSet }}</td>
      </tr>
      <tr>
        <td>Moon Phase</td>
        <td> {{ times.moonPhase?.toFixed(2) }}</td>
      </tr>
      <tr>
        <td>&nbsp;</td>
        <td>&nbsp;</td>
      </tr>
      <tr>
        <td>Date</td>
        <td> {{ new Intl.DateTimeFormat('en', {day: 'numeric', month: 'long',year : 'numeric'}).format(Date.now()) }}</td>
      </tr>
      <tr>
        <td>Hijri Date</td>
        <td> {{ new Intl.DateTimeFormat('ar-TN-u-ca-islamic', {day: 'numeric', month: 'long'}).format(Date.now()) }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
</style>
