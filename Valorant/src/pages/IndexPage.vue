
<template>
  <q-page>
    <div class="image-container">
      <img src="~assets/suke-8.jpg" class="background-image" />
      <div class="login-container">
        <valorant-login />
      </div>
    </div>
  </q-page>
</template>

<style lang="scss" scoped>
.image-container {
  position: relative;
}

.background-image {
  display: block;
  width: 100%;
}

.login-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1;
}
</style>

<script>
import { defineComponent } from 'vue'
import ValorantLogin from './components/ValorantLogin.vue'

export default defineComponent({
  name: 'IndexPage',
  components: {
    ValorantLogin
  }
})
</script>