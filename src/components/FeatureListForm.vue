<template>
  <form v-on:submit.prevent="addFeature">
    <label for="feature-name">name</label>
    <input type="text" id="feature-name" />

    <label for="feature-description">description</label>
    <input type="text" id="feature-description" />

    <label for="feature-enabled">enabled</label>
    <select id="feature-enabled">
      <option selected>true</option>
      <option>false</option>
    </select>
    <button v-on:click="addFeature">add feature</button>
  </form>
</template>

<script>
export default {
  name: 'featurelist-form',
  props: ['onAdd'],
  methods: {
    addFeature () {
      const nameEl = document.getElementById('feature-name')
      const descriptionEl = document.getElementById('feature-description')
      const enabledEl = document.getElementById('feature-enabled')
      if (nameEl.value !== '') {
        this.onAdd({name: nameEl.value, description: descriptionEl.value, enabled: enabledEl.value === 'true'})
        nameEl.value = ''
        descriptionEl.value = ''
      }
    }
  }
}
</script>

<style scoped></style>
