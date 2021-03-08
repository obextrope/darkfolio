<template>
  <div class="layout">
    <Header />
    <slot />
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Footer from "@/components/Footer";

export default {
  components: {
    Header,
    Footer
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');
html {
  font-family: 'Press Start 2P', cursive;
  font-size: 14px;
  font-weight: 500;
  box-sizing: border-box;
}

@supports (font-variation-settings: normal) {
  html {
    font-family: 'Press Start 2P', cursive;
  }
}

*,
*:before,
*:after {
  box-sizing: inherit;
}
body {
  background-color: #A9B4D3;
  color: #BDDC9A;
  margin: 0;
  padding: 0;
}
a {
  color: inherit;
  text-decoration: none;
  border-bottom: 1.5px solid transparent;
  padding-bottom: 0.25rem;
  transition: border 0.15s ease;
  &:hover {
    border-bottom: 1.5px solid currentColor;
  }
}
</style>
