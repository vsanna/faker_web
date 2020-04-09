<template>
  <table class="uk-table uk-table-divider">
    <tbody>
      <tr v-for="(record, idx) in this.data" :key="idx">
        <td v-for="(cell, idx2) in record" :key="idx2">{{ cell }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { Prop } from "vue-property-decorator";

@Component
export default class extends Vue {
  @Prop()
  data!: Array<Array<any>> = [];

  intervalId: number | null = null;
}
</script>
