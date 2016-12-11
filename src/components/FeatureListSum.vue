<template>
  <tfoot>
    <tr>
      <td>Total: {{totalCount}}</td>
      <td>Enabled: {{totalEnabled}}</td>
      <td></td><td></td>
    </tr>
  </tfoot>
</template>

<script>
export default {
  name: 'featurelist-sum',
  props: ['totalCount', 'totalEnabled']
}
</script>

<style>
  tr {
    background-color: #ddd;
    color: #666;
  }
</style>
