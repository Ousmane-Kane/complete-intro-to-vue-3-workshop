<script>
export default {
    props:{ characters: {
        type: Array,
        required: true
    }},
    computed: {
          fightingStyle() {
            const attributes = ['DF', 'Swordsman', 'Thunderclouds', 'FireLeg']
            const statistics = {
              DF: 0,
              Swordsman: 0,
              FireLeg: 0,
              Thunderclouds: 0
            }
            this.characters.forEach(character => {
              attributes.forEach(attribute => {
                if (character.attribute.indexOf(attribute) > -1) {
                  statistics[attribute] +=1
                }
              })

            })
            return statistics
          }
        },
}
</script>

<template>
    <h2>Statistics</h2>
      <li v-for="(stat, type) in fightingStyle"> 
       {{ type}}: {{ stat }}
      </li>
</template>