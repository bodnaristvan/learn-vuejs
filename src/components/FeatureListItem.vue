<template>
  <tr v-bind:class="!feature.enabled ? 'disabled' : '' ">
    <td>{{feature.name}}</td>
    <td>{{feature.description|capitalize}}</td>
    <td class="actions">
      <a href="javascript:;" v-on:click.prevent="onToggleState(findex)">{{ feature.enabled ? 'disable' : 'enable' }}</a>
    </td>
    <td class="actions">
      <a href="javascript:;" v-on:click.prevent="onRemove(findex)">delete</a>,
      <a href="javascript:;" v-on:click.prevent="onEdit(findex)">edit</a>
    </td>
  </tr>
</template>

<script>
export default {
  name: 'featurelist-item',
  props: ['feature', 'findex', 'onRemove', 'onEdit', 'onToggleState'],
  filters: {
    capitalize (value) {
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style scoped>
  tbody tr {
    background-color: #eee;
    color: #333;
  }
  tbody tr.disabled {
    background-color: #fafafa;
    color: #999;
  }
</style>
