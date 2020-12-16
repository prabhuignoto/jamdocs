<template>
  <div  class="github-btns">  
    <a
      href="https://github.com/prabhuignoto/vue-dock-menu/stargazers"
      :class="size"
      title="Git-repository"
      aria-label="vue-dock-menu on Github"
    >
      <star-icon class="icon" />
      {{ star }}
    </a>
  </div>
</template>

<script>
import { GithubIcon, StarIcon } from "vue-feather-icons";

export default {
  components: {
    GithubIcon,
    StarIcon,
  },
  props: {
    size: {
      type: String,
      default: "small",
    },
    text: {
      type: String,
      default: "Fork me on Github",
    },
    star: {
      type: String,
      default: "Star this project on Github",
    },
  },
};
</script>

<style lang="scss" scoped>
a {
  display: inline-block;
  padding: 6px 10px;
  text-decoration: none;
  border-radius: 3px;
  font-size: 12px;
  line-height: 18px;
  font-weight: 700;
  transition: color 0.15s ease-in-out, background 0.15s ease-in-out;
  margin: 0.5rem 0;

  &:focus {
    outline: none;
  }

  .dark & {
    color: $textBright;
    background: $backgroundBright;
  }

  .bright & {
    color: $textDark;
    background: $backgroundDark;
  }

  svg {
    width: 18px;
    height: 18px;
    vertical-align: -6px;
    margin-right: 4px;
  }

  &.large {
    @include respond-above(sm) {
      font-size: 18px;
      padding: 12px 20px;
      line-height: 24px;

      svg {
        width: 24px;
        height: 24px;
      }
    }
  }
}

.github-btns  {
  display: flex;
  flex-direction: column;
}
</style>

