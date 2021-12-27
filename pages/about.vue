<template>
  <div>
    <h4>About Page</h4>
    <p>{{ cart }}</p>
    <v-btn color="primary" depressed title="Add" @click="increment()"
      >Increment</v-btn
    >
    <h5>{{ emailAddress }}</h5>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from "nuxt-property-decorator";
import Counter from "@/components/counter.vue";
@Component({
  components: { Counter },
})
export default class About extends Vue {
  message: String = "Hello Ronith N";
  location: String = "Singapore";
  firstName: string = "Ronith";
  lastName: string = "N";
  value: number = 0;
  private temp: Array<object> = [
    {
      name: "Preetish",
      age: "26",
    },
    {
      name: "John",
      age: "30",
    },
  ];
  @Prop({ required: false, type: String, default: "Developer" })
  readonly job!: string;

  @Prop({ required: false, type: Number, default: 0 }) cart!: Number;

  increment(value: any): void {
    console.log(this.value);
    this.value = this.value + value;
  }

  decrement(value: any): void {
    this.value = this.value - value;
  }

  get emailAddress(): string {
    return this.firstName + this.lastName + "@gmail.com";
  }

  getValue(): number | string {
    if (this.value === 0) return "zero";
    return this.value;
  }

  getBadgeColor(): string {
    if (this.value === 0) return "grey";
    return "orange";
  }

  isDisabled(): boolean {
    return this.value === 0 ? true : false;
  }

  @Watch("cart")
  cartChanged(newValue: number) {
    console.log(newValue);
  }
}
</script>
