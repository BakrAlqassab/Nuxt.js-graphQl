<template>
  <div>
    <div style="border: dashed; width: 100%; height: fit-content">
      <h3 class="text-2xl">{{ character.name }}</h3>
      <h3 class="text-2xl">{{ character.id }}</h3>
    </div>

    <div style="margin: 24px; width 40%;display: inline-block;">
      <button
        @click="characterId = characterId + 1"
        class="bg-gray-700 p-4 border text-white"
      >
        Character ID increment
      </button>
      <!-- <Tutorial /> -->

      <ul>
        <li v-for="character in characters.results" :key="character.id">
          {{ character.name }}, {{ character.status }},
        </li>
      </ul>
    </div>

    <div style="margin: 24px width 40%; display: inline-block">
      <img :src="character.image" :alt="character.id" />
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  data() {
    return {
      characterId: 1,
    }
  },
  apollo: {
    characters: gql`
      query getcharecter {
        characters {
          results {
            id
            name
            status
            gender
          }
        }
      }
    `,
    character: {
      query: gql`
        query getCharacter($id: ID!) {
          character(id: $id) {
            id
            name
            image
          }
        }
      `,
      variables() {
        return {
          id: this.characterId,
        }
      },
    },
  },
}
</script>
