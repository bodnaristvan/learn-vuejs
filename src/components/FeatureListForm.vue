<template>
    <tr>
      <td>
        <input type="text" ref="feature-name" v-model="feature.name" />
      </td>
      <td>
        <input type="text" ref="feature-description" v-model="feature.description"/>
      </td>
      <td>
        <input type="checkbox" ref="feature-enabled" v-model="feature.enabled">
      </td>
      <td>
        <button v-if="!feature.editing" v-on:click="addFeature">add feature</button>
        <button v-else v-on:click.prevent="updateFeature(findex)">update {{feature.name}} feature</button>
      </td>
    </tr>
</template>

<script>
export default {
  name: 'featurelist-form',
  props: ['feature', 'findex', 'onAdd', 'onUpdate'],
  methods: {
    addFeature () {
      const nameEl = this.$refs['feature-name']
      const descriptionEl = this.$refs['feature-description']
      const enabledEl = this.$refs['feature-enabled']
      if (nameEl.value !== '') {
        this.onAdd({name: nameEl.value, description: descriptionEl.value, enabled: enabledEl.value === 'true', editing: false})
        nameEl.value = ''
        descriptionEl.value = ''
      }
    },
    updateFeature (index) {
      const nameEl = this.$refs['feature-name']
      const descriptionEl = this.$refs['feature-description']
      const enabledEl = this.$refs['feature-enabled']
      if (nameEl.value !== '') {
        this.onUpdate({name: nameEl.value, description: descriptionEl.value, enabled: enabledEl.value === 'true', editing: false}, index)
        nameEl.value = ''
        descriptionEl.value = ''
      }
    }
  }
}
</script>

<style scoped></style>
