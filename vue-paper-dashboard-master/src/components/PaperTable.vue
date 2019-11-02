<template>
  <table class="table" :class="tableClass">
    <thead>
    <slot name="columns">
      <th v-for="column in columns" :key="column">{{column}}</th>
    </slot>
    </thead>
    <tbody>
    <tr v-for="(item, index) in data" :key="index">
      <slot :row="item">
          <td v-for="(column, index) in columns"
              :key="index"
              v-if="hasValue(item, column)">

              <template v-if="!!itemLink(item, column) && column === '제목'"> <!--제목 대신 item['linkTarget']-->
                <a :href="itemLink(item, column)">{{itemValue(item, column)}}</a>
              </template>
              <template v-else>
                {{itemValue(item, column)}}
              </template>

          </td>
      </slot>
    </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  name: 'paper-table',
  props: {
    columns: Array,
    data: Array,
    type: {
      type: String, // striped | hover
      default: "striped"
    },
    title: {
      type: String,
      default: ""
    },
    subTitle: {
      type: String,
      default: ""
    }
  },
  computed: {
    tableClass() {
      return `table-${this.type}`;
    }
  },
  methods: {
    hasValue(item, column) {
      return item[column.toLowerCase()] !== "undefined";
    },
    itemValue(item, column) {
      return item[column.toLowerCase()];
    },
    itemLink(item, column){
      return item['link'];
    }
  }
};
</script>
<style>
</style>
