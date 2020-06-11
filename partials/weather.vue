<template>
  <div class="weather">
    <p class="temp">
      <span class="temp-value">{{temp}}ºC</span>
      <span class="humidity-value">{{humidity}}%</span>
    </p>
  </div>
</template>

<script>
export default {
  props: [
    "temp",
    "humidity"
  ]
};
</script>
