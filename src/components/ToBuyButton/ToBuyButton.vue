<template>
  <button
    :class="`button-${this.btnStyle} ${icon ? 'button-icon' : ''}`"
    class="button"
    @click="$emit('click')"
  >
    {{ text }}
    <i v-if="icon" :data-feather="icon" />
  </button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
// import feather from "feather-icons";

@Component({
  name: "ToBuyButton"
})
export default class ToBuyButton extends Vue {
  @Prop(String) text!: string;
  @Prop({ default: "primary" }) btnStyle!: string;
  @Prop(String) icon!: string;
}
</script>

<style lang="scss">
@use '@/assets/scss/tokens.scss' as tokens;

.button {
  padding: 10px 30px;
  color: tokens.$light-color;
  @include tokens.lightBorderRadius;
  border: tokens.$lightBorder;

  &-icon {
    padding: 10px 13px;
    border-radius: 50%;
  }

  &-primary {
    background-color: lighten(tokens.$color-primary, 10%);
    border-color: tokens.$color-primary;
  }

  &-danger {
    background-color: lighten(tokens.$color-danger, 10%);
    border-color: darken(tokens.$color-danger, 10%);
  }
}
</style>
