<template>
  <div
    v-if="!$apollo.queries.character.loading"
    class="rounded border m-2"
    style="display: flex"
  >
    <img :src="character.image" :alt="character.id" /> 
    <div style="margin: 8px">
      <span>{{ character.status }}</span>
      <h1 style="font-size: 16px; font-weight: bold">{{ character.name }}</h1>
      <h1>{{ character.gender }}</h1>
      <h1>{{ character.origin.name }}</h1>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'character',
  apollo: {
    character: {
      query: gql`
        query getCharacter($id: ID!) {
          character(id: $id) {
            id
            name
            status
            image
            species
            gender
            origin {
              name
            }
          }
        }
      `,
      variables() {
        return {
          id: this.$route.params.id,
        }
      },
    },
  },
}
</script>
