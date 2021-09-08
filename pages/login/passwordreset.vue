<template>
<div class="reset-wrapper">
  <div class="reset-wrapper__blur">

  </div>
</div>
</template>

<script>
export default {
  name: "reset"
}
</script>

<style lang="scss">
.reset-wrapper {
  background: url("https://anvilhook.ru/wp-content/uploads/2020/09/%D1%84%D1%83%D0%B4%D1%81%D1%82%D0%B0%D0%B9%D0%BB%D0%B8%D0%BD%D0%B3-%D0%B1%D0%B0%D0%BD%D0%BD%D0%B5%D1%80.jpg") no-repeat center top / cover;
  height: 100vh;
  width: 100vw;
}
.reset-wrapper__blur {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  height: 100vh;
  width: 100%;
}
</style>
