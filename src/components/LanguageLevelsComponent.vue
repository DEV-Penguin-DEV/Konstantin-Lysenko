<template>
  <div class="progress-bar__levels">
    <ul class="progress-bar__levels-container">
      <li :class="'progress-bar__level'" v-for="level in Levels" :key="level">
        {{ level }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Levels: ["A1", "A2", "B1", "B2", "C1", "C2"],
    };
  },
};
</script>

<style lang="scss" scoped>
.progress-bar__levels-container {
  display: flex;
  justify-content: space-between;
  width: 88%;
  position: absolute;
  @include centering-horizontal-absolut-element();
  z-index: 2;

  @media (max-width: $big-tablet-size) {
    width: 85%;
  }

  @media (max-width: $mini-tablet-size) {
    width: 82%;
  }

  @media (max-width: $big-phone-size) {
    width: 88%;
  }

  @media (min-width: $desktop-size) {
    width: 90%;
  }
}

.progress-bar__level {
  color: $main-text-color;
  font-size: 2.5vw;
  font-style: normal;
  font-weight: 600;
  line-height: 116%; /* 116.667% */
  letter-spacing: 0.1125rem;

  @media (max-width: $laptop-size) {
    margin-top: 5px;
  }

  @media (min-width: $desktop-size) {
    font-size: 2.1vw;
  }
  @media (max-width: $phone-size) {
    font-size: 3vw;
  }
}
</style>
