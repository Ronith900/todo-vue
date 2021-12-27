<template>
  <div>
    <v-badge :content="getTotalItems()"></v-badge>

    <Counter @updateState="updateEmpHealthStatus" />
    <Counter @updateState="updateEmpHealthStatus" />
    <Counter @updateState="updateEmpHealthStatus" />
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from "nuxt-property-decorator";
import Counter from "@/components/counter.vue";
@Component({
  components: { Counter },
})
export default class Counters extends Vue {
  total: number = 0;

  updateEmpHealthStatus(value: any) {
    if (value === "I") {
      this.total = this.total + 1;
    } else {
      this.total = this.total - 1;
    }
  }

  getTotalItems() {
    return this.total === 0 ? "zero" : this.total;
  }
}
</script>
