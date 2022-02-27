<template>
  <div>
    <div class="cookie" :class="{ consent }">
      Cookies cookies
      <button @click="allow">agree</button>
    </div>
    {{ new Date().getFullYear() }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      consent: true,
    }
  },
  methods: {
    allow() {
      this.consent = true
      localStorage.setItem('allowCookies', true)
    },
  },
  mounted() {
    if (!localStorage.getItem('allowCookies')) this.consent = false
  },
}
</script>

<style>
.consent {
  display: none;
}
</style>
