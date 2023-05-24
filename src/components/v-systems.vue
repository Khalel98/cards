<template>
  <div class="container">
    <div class="tech-slideshow">
      <div class="mover-1"></div>
      <div class="mover-2"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.tech-slideshow {
  height: 100px;
  max-width: 800px;
  margin: 0 auto;
  position: relative;
  overflow: hidden;
  transform: translate3d(0, 0, 0);
}

.tech-slideshow > div {
  height: 100px;
  width: 2526px;
  background: url("../assets/banner.png");
  background-size: contain;
  position: absolute;
  top: 0;
  left: 0;

  transform: translate3d(0, 0, 0);
}
.tech-slideshow .mover-1 {
  animation: moveSlideshow 12s linear infinite;
}
.tech-slideshow .mover-2 {
  opacity: 0;
  transition: opacity 0.5s ease-out;
  background-position: 0 -200px;
  animation: moveSlideshow 150s linear infinite;
}

@keyframes moveSlideshow {
  100% {
    transform: translateX(-66.6666%);
  }
}
</style>
