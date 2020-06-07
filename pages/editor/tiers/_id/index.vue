<template>
  <div>
    <p v-if="$fetchState.pending">Fetching posts...</p>
    <p v-else-if="$fetchState.error">
      Error while fetching posts: {{ $fetchState.error.message }}
    </p>
    <ul v-else>
      <tier v-for="tier in tiers" :key="`tier_${tier.level}`" :tier="tier" />
    </ul>
  </div>
</template>

<script>
import tier from '~/components/editor/tier.vue'

export default {
  components: {
    tier
  },
  async fetch() {
    this.tiers = await this.$axios.$get(
      `https://paste.helpch.at/raw/${this.$route.params.id}`
    )
  },
  data() {
    return {
      tiers: []
    }
  }
}
</script>
