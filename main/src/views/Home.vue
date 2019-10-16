<template>
  <div class="home">
    <test-news></test-news>
  </div>
</template>

<script>
import testNews from "../components/testNews";

export default {
  name: "home",
  components: {
    testNews
  }
};
</script>
