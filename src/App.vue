<script lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import SunCalc from 'suncalc';
import { DateTime } from "luxon";
import { get } from 'lodash';
import Times from './components/Times.vue'
import { defineComponent, ref } from "vue";

export default defineComponent({
  components: {
    Times,
  },
  setup() {
    let rval = {}
  },
  data() {
    return {
      times: {}
    }
  },
  created() {
    SunCalc.addTime(-18, 'astronomicalDawn', 'astrologicalDusk');
    SunCalc.addTime(-15, 'fifteenDawn', 'fifteenDusk');
    SunCalc.addTime(-6, 'civilDawn', 'civilDusk');

    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition((position) => {
        const times = SunCalc.getTimes(new Date(), position.coords.latitude, position.coords.longitude);
        const moonTimes = SunCalc.getMoonTimes(new Date(), position.coords.latitude, position.coords.longitude);
        const moonIllumination = SunCalc.getMoonIllumination(new Date());

        console.info(position);
        const data:any = {
          astronomicalDawn: DateTime.fromJSDate(get(times, 'astronomicalDawn')).toLocaleString(DateTime.TIME_24_SIMPLE),
          nauticalDawn: DateTime.fromJSDate(times.nauticalDawn).toLocaleString(DateTime.TIME_24_SIMPLE),
          civilDawn: DateTime.fromJSDate(get(times, 'civilDawn')).toLocaleString(DateTime.TIME_24_SIMPLE),
          fifteenDawn: DateTime.fromJSDate(get(times, 'fifteenDawn')).toLocaleString(DateTime.TIME_24_SIMPLE),
          sunrise: DateTime.fromJSDate(times.sunrise).toLocaleString(DateTime.TIME_24_SIMPLE),
          noon: DateTime.fromJSDate(times.solarNoon).toLocaleString(DateTime.TIME_24_SIMPLE),
          sunset: DateTime.fromJSDate(times.sunset).toLocaleString(DateTime.TIME_24_SIMPLE),
          civilDusk: DateTime.fromJSDate(get(times, 'civilDusk')).toLocaleString(DateTime.TIME_24_SIMPLE),
          nauticalDusk: DateTime.fromJSDate(times.nauticalDusk).toLocaleString(DateTime.TIME_24_SIMPLE),
          fifteenDusk: DateTime.fromJSDate(get(times, 'fifteenDusk')).toLocaleString(DateTime.TIME_24_SIMPLE),
          astrologicalDusk: DateTime.fromJSDate(get(times, 'astrologicalDusk')).toLocaleString(DateTime.TIME_24_SIMPLE),
          nadir: DateTime.fromJSDate(times.nadir).toLocaleString(DateTime.TIME_24_SIMPLE),
        };

        if(moonTimes.set) {
          data['moonSet'] = DateTime.fromJSDate(moonTimes.set).toLocaleString(DateTime.TIME_24_SIMPLE);
        }
        if(moonTimes.rise) {
          data['moonRise'] = DateTime.fromJSDate(moonTimes.rise).toLocaleString(DateTime.TIME_24_SIMPLE);
        }
        data['moonPhase'] = moonIllumination.phase;

        this.times = data;
      });
    }

  }
});
</script>

<template>
  <Times :times="times" />
</template>

<style>

</style>
