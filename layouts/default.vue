<template>
  <main>
    <nuxt />
    <div class="footer">
      <p>Footer</p>
    </div>
  </main>
</template>

<script>
export default {
  name: 'Default',
}
</script>

<style scoped>
.footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100vw;
  height: 100px;
  background: rgb(0, 0, 0);
  display: flex;
  align-items: center;
  justify-content: center;
}

.footer p {
  color: #fff;
  font-size: 2rem;
}
</style>
