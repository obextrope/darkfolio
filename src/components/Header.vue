<template>

  <header class="header">
    <g-link
      to="/"
      tag="h1"
      class="name"
      :class="{ first: data.first_letter_only }"
    >
      <span
        class="word"
        :class="{ 'first-line': index === 0 && multiLine }"
        v-for="(word, index) in siteName"
        :key="index"
      >
        <span class="first-letter" v-if="data.first_letter_only && word[0]">{{
          word[0]
        }}</span>
        <span class="letter" v-if="data.first_letter_only">{{
          word.slice(1)
        }}</span>
        <span v-if="!data.first_letter_only">{{ word }}</span>
      </span>
    </g-link>
    <div class="contact">
      <a class="link" :href="`mailto:${data.email}`">email button :⁾</a>
    </div><style type="text/css">a { cursor: url('data:image/x-icon;base64,AAACAAEAICAQAA0AAgDoAgAAFgAAACgAAAAgAAAAQAAAAAEABAAAAAAAAAIAAAAAAAAAAAAAEAAAAAAAAAAAAAAAG6L6AO/g2QAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAREREREREREAAAAAAAAAAAERERERERERAAAAAAAAAAABEiIiIiIiEQAAAAAAAAAAARIiIiIiIhEAAAAAAAAAARIiIiIiIiIREQAAAAAAAAESIiIiIiIiEREAAAAAAAESIiIiIiIiIiIRAAAAAAABEiIiIiIiIiIiEQAAAAABEiIiIiIiIiIiIhEAAAAAARIiIiIiIiIiIiIRAAAAAAESIiIiIiIiIiIiIhEAAAABEiIiIiIiIiIiIiIRAAABEiIiIiIiIiIiIiIiEQAAARIiIiIiIiIiIiIiIhEAARIiIiESIiIiIiIiIiIRAAESIiIhEiIiIiIiIiIiEQABEiIhERIiIiIiIiIiIhEAARIiIRESIiIiIiIiIiIRAAABERABEiIRIhEiESIiEQAAAREQARIiESIRIhEiIhEAAAAAAAESIhEiESIRIiIRAAAAAAABEiIRIhERERERAAAAAAAAARIiEREQERAREQAAAAAAAAESIhEREAAAAAAAAAAAAAABEiIRAAAAAAAAAAAAAAAAARIiEQAAAAAAAAAAAAAAAAESIhEAAAAAAAAAAAAAAAABEiIRAAAAAAAAAAAAAAAAARIiEQAAAAAAAAAAAAAAAAESIhEAAAAAAAAAAAAAAAAAAREQAAAAAAAAAAAAAAAAAAEREAAAAAAAAAD/+AAP//gAD//4AA//+AAP/+AAA//gAAP/gAAD/4AAA/4AAAP+AAAD/gAAAP4AAAD4AAAA+AAAAOAAAADgAAAA4AAAAOAAAAD4YAAA+GAAAP/gAAD/4AAD/+AEQ//gB///4D///+A////gP///4D///+A////gP///+H////h//w=='), auto; }</style>
    
  </header>
</template>

<script>
import data from "@/data/theme.json";

export default {
  name: "Header",
  data() {
    return {
      data
    };
  },
  computed: {
    siteName() {
      return data.header_title.split(" ");
    },
    multiLine() {
      return this.siteName.length >= 1;
    }
  }
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  padding: 4rem 2rem 5rem 2rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  z-index: 100;
  opacity: 1;
  color: #EF5C7B;
  transition: opacity 0.5s ease;
  &.hidden {
    opacity: 0;
  }
}
.name {
  font-size: 1.3rem;
  font-weight: 500;
  user-select: none;
  margin: 0;
  .word {
    margin-right: 0.5rem;
    &.first-line {
      display: block;
      margin-bottom: 0.5rem;
    }
    &:last-of-type {
      margin: 0;
    }
  }
  &.first {
    .letter {
      transition: opacity 0.15s ease;
      opacity: 0;
    }
    .first-letter {
      opacity: 1;
    }
    &:hover {
      .letter {
        opacity: 1;
      }
    }
  }
}
</style>
