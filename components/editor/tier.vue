<template>
  <li>
    <div v-if="!level.edit" @click="level.edit = true">
      <code>{{ tier.level }}</code>
    </div>
    <div v-else>
      <input v-model="level.value" type="number" />
    </div>
  </li>
</template>

<script>
export default {
  name: 'Tier',
  props: {
    tier: Object
  },
  data() {
    return {
      level: {
        edit: false,
        value: this.tier.level
      }
    }
  }
}
</script>
