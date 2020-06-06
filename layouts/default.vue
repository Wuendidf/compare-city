<template>
  <div>
    <MainNav ></MainNav>

    <nuxt />

    <MainFooter></MainFooter>

  </div>
</template>

<script>
import MainNav from '@/components/MainNav'
import MainFooter from '@/components/MainFooter'

export default {
  components: {
    MainNav,
    MainFooter
  }
}
</script>
