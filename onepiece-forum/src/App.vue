<script >
import CharacterCard from "./components/CharacterCard.vue"
import fightingStyle from "./components/FightingStyle.vue"
import BaseLayout from "./components/BaseLayout.vue";
  export default {
        components: {
          fightingStyle,
          CharacterCard,
          BaseLayout
        },
        data: () => ({
          newCharacter: {
            name: '',
            attribute: []
          },
          characterList: [
            {
              name: 'Luffy',
              attribute: ['DF']
            },
            {
              name: 'Zoro',
              attribute: ['Swordsman']
            },
            {
              name: 'Nami',
              attribute: ['Thunderclouds']
            },
            {
              name: 'Sanji',
              attribute: ['FireLeg']
            },
            {
              name: 'Brook',
              attribute: ['Swordsman']
            }
          ],
          favoriteList: []
        }),
        
        methods: {
          addNewCharacter() {
            this.characterList.push(this.newCharacter)
            this.newCharacter = { name: ''}
          },
          addfavoriteCharacter(payload) {
            this.favoriteList.push(payload)
            
          }
        }

      }
</script>

<template>
      <BaseLayout>
        <template v-slot:one>
              <h2> New Character</h2>
          <label for="character-name"> Name</label>
          <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter">
          <pre>
            {{ newCharacter }}
      </pre>
        </template>
      </BaseLayout>
      <fightingStyle :characters="characterList"/>
      
      <h2>Characters</h2>
      <p v-if="characterList.length === 0"> There are no characters</p>
      <ul>
        <li v-for="character in characterList" :key="character.index" > 
         <CharacterCard :character="character" @favorite  ="addfavoriteCharacter"/>
        </li>
      </ul>
      <h2> Favorite Characters</h2>
      <ul v-if="favoriteList.length > 0">
        <li v-for="character in favoriteList" :key="character.index"> {{ character }}</li>
      </ul>
      <p v-else> No favorite characters yet! </p>
</template>


