<template>
  <div class="container" style="background-color: #f0ebeb; margin: 5% 10%">
    <div>
      <h1 class="text-4xl font-semibold text-gray-800 mb-8">
        DoingITeasyChannel - Nuxt Series
      </h1>

      <div class="flex">
        <!-- <Tutorial /> -->

        <ul class="w-64">
          <li v-for="character in characters.results" :key="character.id">
            <nuxt-link
              class="hover:font-bold hover:text-gray-900 leading-loose"
              :to="character.id"
            >
              {{ character.name }}
            </nuxt-link>
          </li>
        </ul>

        <div class="flex-grow bg-white min-h-full">
          <nuxt-child :key="$route.params.id"> </nuxt-child>
        </div>
      </div>
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

  fetch({ redirect, route }) {
    if (!route.params.id) {
      redirect('/1')
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
