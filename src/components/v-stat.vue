<template>
  <div class="section__row">
    <div class="section__statistics__item">
      <div class="section__statistics__item__number">
        {{ animatedValues[0] }} К <span class="primary_color">+</span>
      </div>
      <div class="section__statistics__item__title">
        пользователей - ученики
      </div>
    </div>
    <div class="section__statistics__item">
      <div class="section__statistics__item__number">
        {{ animatedValues[1] }}
      </div>
      <div class="section__statistics__item__title">
        пользователей - учителя
      </div>
    </div>
    <div class="section__statistics__item">
      <div class="section__statistics__item__number">
        {{ animatedValues[2] }}
      </div>
      <div class="section__statistics__item__title">
        пользователей - персоналы
      </div>
    </div>
    <div class="section__statistics__item">
      <div class="section__statistics__item__number">
        {{ animatedValues[3] }} К <span class="primary_color">+</span>
      </div>
      <div class="section__statistics__item__title">
        пользователей в системе
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      statistics: [
        { value: 48 },
        { value: 3508 },
        { value: 1046 },
        { value: 51 },
      ],
      animatedValues: [],
    };
  },
  mounted() {
    this.animateStatistics();
  },
  methods: {
    animateStatistics() {
      this.statistics.forEach((stat, index) => {
        this.animatedValues[index] = 0;
        const targetValue = stat.value;
        const duration = 5000; // Animation duration in milliseconds
        const frameDuration = 1000 / 60; // Assuming 60 frames per second

        const totalFrames = Math.round(duration / frameDuration);
        const frameIncrement = targetValue / totalFrames;

        let currentFrame = 0;
        const animationInterval = setInterval(() => {
          currentFrame++;
          this.animatedValues[index] = Math.round(
            frameIncrement * currentFrame
          );
          if (currentFrame === totalFrames) {
            this.animatedValues[index] = targetValue;
            clearInterval(animationInterval);
          }
        }, frameDuration);
      });
    },
  },
};
</script>

<style></style>
