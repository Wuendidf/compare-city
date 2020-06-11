<template>
  <div class="MainSlider" :class="size">
    <header class="masthead" :style='"background-image: url("+ image +");"'>
      <div class="container">
        <div class="masthead-subheading">Bienvenido</div>
        <div class="masthead-heading text-uppercase">Compare city</div>
        <a class="btn btn-primary btn-xl text-uppercase js-scroll-trigger" href="/cities">Comencemos</a>
      </div>
    </header>
      <img src="/assets/img/header-bg.jpg" alt=""/>
  </div>
</template>

<script>
export default {
	props: ["image", "size" ]
}
</script>
