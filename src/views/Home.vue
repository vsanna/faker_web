<template>
  <div class="uk-container uk-container-small home">
    <h1>data</h1>
    <DataTable :data="data" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import * as faker from "faker";
import DataTable from "@/components/DataTable";

@Component({
  components: { DataTable },
})
export default class Home extends Vue {
  data: Array<Array<any>> = [];
  intervalId: number | null = null;
  readonly datalength = 10;

  created() {
    this.init();
  }

  init() {
    this.intervalId = setInterval(() => {
      if (this.data.length >= this.datalength) {
        this.data = [
          ...this.data.slice(
            this.data.length - (this.datalength - 1),
            this.data.length
          ),
        ];
      }
      this.data.push(this.generateFakeRecord());
    }, 3000);
  }

  stop() {
    if (this.intervalId !== null) {
      clearInterval(this.intervalId);
    }
    this.intervalId = null;
  }

  generateFakeRecord(): Array<any> {
    return [
      faker.internet.email(),
      faker.internet.password(),
      faker.name.findName(),
      (faker.date.past() as Date).toDateString(),
    ];
  }
}
</script>
