<template>
  <div>
    <div class="header-bg">
      <!-- background header image goes here -->
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.header-bg {
  background: url("../../public/images/bg-header-desktop.svg"),
    hsl(180, 8%, 52%);
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 150px;
}

@media only screen and (max-width: 375px),
  (min-width: 375px) and (max-width: 768px) {
  .header-bg {
    background: url("../../public/images/bg-header-mobile.svg"),
      hsl(180, 8%, 52%);
  }
}
</style>