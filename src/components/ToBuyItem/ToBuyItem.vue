<template>
  <div class="to-buy-item">
    <div class="to-buy-item-shoping">
      <to-buy-buttom :icon="'shopping-cart'" @click="$emit('shop')" />
    </div>
    <div class="to-buy-item-name">{{ name }}</div>
    <div class="to-buy-item-remove">
      <to-buy-buttom
        :icon="'x'"
        :btnStyle="'danger'"
        @click="$emit('remove')"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import ToBuyButtom from "@/components/ToBuyButton/ToBuyButton.vue";

@Component({
  name: "ToBuyItem",
  components: {
    ToBuyButtom
  }
})
export default class ToBuyItem extends Vue {
  @Prop({ required: true }) name!: string;
}
</script>

<style lang="scss">
@use '@/assets/scss/tokens.scss' as tokens;

.to-buy-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: tokens.$lightBorder;

  &-name {
    font-family: "Balsamiq Sans", cursive;
    font-size: 20px;
  }
}
</style>
