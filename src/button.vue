<template>
  <button class="m-button" :class="{[`icon-${iconPosition}`]:true}">
    <svg class="icon" v-if="icon">
      <use :xlink:href="`#i-md-${icon}`"></use>
    </svg>
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    icon: {},
    iconPosition: {
      type: String,
      default: 'left',
      validator(v) {
        return v === 'left' || v === 'right';
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.m-button {
  font-size: var(--font-size);
  height: var(--button-height);
  line-height: var(--font-size);
  padding: 0 1em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  background: var(--button-bg);
  display: inline-flex;
  justify-content: center;
  align-content: center;
  vertical-align: middle;

  &:hover {
    border-color: var(--border-color-hover);
  }

  &:active {
    background-color: var(--button-active-bg);
  }

  &:focus {
    outline: none;
  }

  &.icon-left .icon {
    margin-right: 0.3em;
  }
;

  &.icon-right {
    flex-direction: row-reverse;

    .icon {
      margin-right: 0;
      margin-left: 0.3em;
    }
  }
}
</style>
<style>
.icon {
  width: 1em;
  height: 1em;
}
</style>
