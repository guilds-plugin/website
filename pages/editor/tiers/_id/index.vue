<template>
  <div>
    <p v-if="$fetchState.pending">Fetching posts...</p>
    <p v-else-if="$fetchState.error">
      Error while fetching posts: {{ $fetchState.error.message }}
    </p>
    <ul v-else>
      <tier v-for="tier in tiers" :key="tier.level" />
    </ul>
    <!-- <table v-else class="table table-striped table-dark">
      <b-thead>
        <b-tr>
          <b-th>Level</b-th>
          <b-th>Name</b-th>
          <b-th>Cost</b-th>
          <b-th>Max Members</b-th>
          <b-th>Vault Amount</b-th>
          <b-th>Mob XP Multiplier</b-th>
          <b-th>Damage Multiplier</b-th>
          <b-th>Max Bank Balance</b-th>
          <b-th>Members To Rankup</b-th>
          <b-th>Max Allies</b-th>
          <b-th>Use Buffs</b-th>
        </b-tr>
      </b-thead>
      <b-tbody>
        <b-tr v-for="tier in tiers" :key="tier.level">
          <b-td>{{ tier.level }}</b-td>
          <b-td>{{ tier.name }}</b-td>
          <b-td>{{ tier.cost }}</b-td>
          <b-td>{{ tier.maxMembers }}</b-td>
          <b-td>{{ tier.vaultAmount }}</b-td>
          <b-td>{{ tier.mobXpMultiplier }}</b-td>
          <b-td>{{ tier.damageMultiplier }}</b-td>
          <b-td>{{ tier.maxBankBalance }}</b-td>
          <b-td>{{ tier.membersToRankup }}</b-td>
          <b-td>{{ tier.maxAllies }}</b-td>
          <b-td>{{ tier.useBuffs }}</b-td>
        </b-tr>
      </b-tbody>
    </table> -->
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
