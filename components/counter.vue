<template>
  <v-row>
    <v-col>
      <v-badge :color="getBadgeColor()" :content="getValue()"></v-badge>
      <v-btn class="ml-8" x-small color="success" @click="increment(1)"
        >+</v-btn
      >
      <v-btn
        x-small
        color="error"
        @click="decrement(1)"
        :disabled="isDisabled()"
        >-</v-btn
      >
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from "nuxt-property-decorator";
@Component
export default class Counter extends Vue {
  value: number = 0;

  increment(value: any): void {
    this.value = this.value + value;
    this.$emit("updateState", "I");
  }

  decrement(value: any): void {
    this.value = this.value - value;
    this.$emit("updateState", "D");
  }

  getValue(): number | string {
    return this.value === 0 ? "zero" : this.value;
  }

  getBadgeColor(): string {
    return this.value === 0 ? "grey" : "orange";
  }

  isDisabled(): boolean {
    return this.value === 0 ? true : false;
  }
}
</script>
