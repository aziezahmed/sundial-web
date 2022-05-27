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
    </tbody>
  </table>
</template>

<style scoped>
</style>
