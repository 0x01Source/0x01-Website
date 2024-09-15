<template>
    <router-view />
</template>

<script>

export default {

}
</script>

<style>
html, body {
  overflow: hidden;
  scroll-behavior: smooth; /* Added for smooth scrolling */
}

.sections {
  height: 100vh;
  overflow-y: scroll;
  scroll-snap-type: y mandatory;
  scroll-behavior: smooth; /* Added for smooth scrolling */
}

.section {
  scroll-snap-align: start;
}

* {
  font-family: "Poppins", sans-serif;
  font-weight: 600;
  font-style: normal;
}


</style>