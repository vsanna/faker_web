<template>
  <div class="uk-container uk-container-small about">
    <h1>All querys</h1>
    <table class="uk-table uk-table-divider">
      <thead>
        <tr>
          <th v-for="(h, idx) in this.headers" :key="idx">{{h}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(q, idx) in this.queries" :key="idx">
          <td>{{q.name}}</td>
          <td>{{q.desc}}</td>
          <td>{{q.example}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { queries } from "@/labels/queries";

@Component
export default class Desc extends Vue {
  headers = queries.heads;
  queries = queries.queries;
}
</script>