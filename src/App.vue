<template>
  <SpeedInsights />
  <MainHeader :DB="DB.menu.content" />
  <main class="main-content">
    <FirstScreen :DB="DB.first_screen.content" />
    <ExperienceSection :DB="DB.experience.content" />
    <PortfolioSection :DB="DB.portfolio.content" />
    <SkillsSection :DB="DB.skills.content" />
    <LanguageSection :DB="DB.languages.content" />
  </main>

  <AppLoader />
</template>

<script>
import MainHeader from "@/sections/MainHeader";
import FirstScreen from "@/sections/FirstScreen";
import SkillsSection from "@/sections/SkillsSection";
import ExperienceSection from "@/sections/ExperienceSection";
import PortfolioSection from "@/sections/PortfolioSection";
import LanguageSection from "@/sections/LanguageSection";
import AppLoader from "@/sections/AppLoader";
import { SpeedInsights } from "@vercel/speed-insights/vue";
import { db } from "@/db/db.js";

export default {
  components: {
    MainHeader,
    FirstScreen,
    SkillsSection,
    ExperienceSection,
    PortfolioSection,
    LanguageSection,
    AppLoader,
    SpeedInsights,
  },
  data() {
    return {
      DB: db[this.$store.state.lang],
    };
  },
  watch: {
    // Отслеживаем изменения в состоянии lang
    "$store.state.lang": {
      handler(newLang) {
        // Обновляем значение DB на основе нового состояния lang
        this.DB = db[newLang];
      },
      immediate: true, // Позволяет вызвать обработчик сразу при монтировании компонента
    },
  },
};
</script>

<style lang="scss">
body {
  font-family: Inter, sans-serif;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
  color: $white-color;
  background-color: $bg-color;
  padding-bottom: 20vh;
  overflow-x: hidden;

  @media (max-width: $laptop-size) {
    padding-bottom: 10vh;
  }
}

html {
  scroll-behavior: smooth;
  overflow-x: hidden;
}

.container {
  width: 100vw;
  padding: 0 40px;
  box-sizing: border-box;

  @media (max-width: $laptop-size) {
    padding: 0 30px;
  }

  @media (max-width: $tablet-size) {
    padding: 0 20px;
  }

  @media (max-width: $big-phone-size) {
    padding: 0 15px;
  }
}

a {
  color: $white-color;
  text-decoration: none;
}

* {
  margin: 0;
}

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  border: 0;
  clip: rect(0 0 0 0);
  overflow: hidden;
}

.title {
  font-size: 4vw;
  font-family: Arial;
  font-style: normal;
  font-weight: 600;
  line-height: 100%;
  letter-spacing: 0.1875rem;
  color: $main-text-color;
  margin-left: 48px;
  margin-bottom: 5vw;
  display: block;
  width: fit-content;
  position: relative;

  @media (max-width: $tablet-size) {
    margin-left: 35px;
    margin-bottom: 3.8vw;
  }

  @media (max-width: $big-phone-size) {
    margin-left: 20px;
    margin-bottom: 3.5vw;
  }

  @media (max-width: $phone-size) {
    margin-left: 20px;
    font-size: 6.5vw;
    margin-bottom: 40px;
  }

  @media (min-width: $desktop-size) {
    font-size: 3vw;
  }

  &::before {
    @include default-pseudo-element(100%, 3px);
    background-color: #fff;
    bottom: -6px;
    left: 0;

    @media (max-width: $big-phone-size) {
      height: 2px;
    }
  }

  &::after {
    @include default-pseudo-element(0%, 4px);
    background-color: $main-hover-color;
    bottom: -6px;
    left: 0;
    transition: 0.5s;
    z-index: 2;

    @media (max-width: $big-phone-size) {
      height: 3px;
    }
  }

  &:hover {
    &::after {
      width: 100%;
      transition: 0.5s;
    }
  }
}

ul,
ol {
  padding: 0;
  margin: 0;
  list-style: none;
}

button {
  background: none;
  border: none;
  padding: 0;
}
</style>
