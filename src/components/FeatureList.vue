<template>
  <div class="feature-list">
    <h1>Kinja features</h1>
    <table>

      <thead>
        <tr>
          <th>name</th>
          <th>description</th>
          <th>enable</th>
          <th>actions</th>
        </tr>
      </thead>

      <tbody>
        <template
          v-for="(feature, findex) in features">
          <featurelist-item
            v-if="!feature.editing"
            :feature="feature"
            :findex="findex"
            :onRemove="onRemove"
            :onEdit="onEdit"
            :onToggleState="onToggleState"></featurelist-item>
          <featurelist-form
            v-else
            :feature="feature"
            :findex="findex"
            :onAdd="onAdd"
            :onUpdate="onUpdate"></featurelist-form>
        </template>
        <!-- new feature form -->
        <featurelist-form
          :feature="{}"
          :onAdd="onAdd"></featurelist-form>
      </tbody>

      <featurelist-sum
        :totalCount="totalCount"
        :totalEnabled="totalEnabled"></featurelist-sum>

    </table>


  </div>
</template>

<script>
import FeatureListForm from './FeatureListForm'
import FeatureListItem from './FeatureListItem'
import FeatureListSum from './FeatureListSum'

export default {
  name: 'featurelist',
  data () {
    return {
      features: [
        {name: 'superuser', description: 'Superuser switch', type: 'alpha', enabled: true},
        {name: 'no3rdparty', description: 'Disable 3rd party code', type: 'beta', enabled: true},
        {name: 'test1', description: 'test #1', type: 'beta', enabled: true},
        {name: 'test2', description: 'test #2', type: 'alpha', enabled: true},
        {name: 'test3', description: 'test #3', type: 'beta', enabled: false},
        {name: 'test4', description: 'test #4', type: 'alpha', enabled: true},
        {name: 'test5', description: 'test #5', type: 'alpha', enabled: false}
      ],
      totalCount: 0,
      totalEnabled: 0
    }
  },
  computed: {
    totalCount () {
      return this.features.length
    },
    totalEnabled () {
      return this.features.filter((i) => { return i.enabled }).length
    }
  },
  methods: {
    onAdd (featureObj) {
      this.features.push(featureObj)
    },
    onRemove (index) {
      this.features.splice(index, 1)
    },
    onToggleState (index) {
      this.features[index].enabled = !this.features[index].enabled
    },
    onEdit (index) {
      this.$set(this.features[index], 'editing', true)
    },
    onUpdate (featureObj, index) {
      Object.assign(this.features[index], featureObj)
    }
  },
  components: {
    'featurelist-form': FeatureListForm,
    'featurelist-item': FeatureListItem,
    'featurelist-sum': FeatureListSum
  }
}
</script>

<style scoped>
  .feature-list {
    padding: 2em;
  }
  a {
    color: #42b983;
  }
  table {
    width: 90%;
  }
  thead tr {
    background-color: grey;
    color: white;
  }
</style>
