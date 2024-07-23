<script>
  export default {
    data(){
            return {
              counterTitle: 'Counter Standard', 
              count: 10,
              incrementAmount: 10,
              message: 'Hello it works',
              listOfNumbers: [
                {
                  name: 1,
                  id: "fji23",
                  list: [1,2,3],
                },
                {
                  name: 2,
                  id: "zkk23",
                  list: [1,2,3],
                },
                {
                  name: 3,
                  id: "zof23",
                  list: [1,2,3],
                },
                {
                  name: 4,
                  id: "xyz23",
                  list: [1,2,3],
                },
                {
                  name: 5,
                  id: "kol23",
                  list: [1,2,3],
                }
              ]
            }
          },
          computed: {
            displayTitle() {
              if (this.count > 20) {
                return 'Counter Standard - Very Long'
              }
              else {
                return 'Counter Standard'
              }
            }
          },
          methods: {
            incrementCount() {
              this.count+= this.incrementAmount
            }
          },
          watch: {
            count(newValue) {
              console.log(newValue)
              if (newValue > 20) {
                this.counterTitle += ' Very Long'
              }
            }
          }
  }
</script>

<template>
      <h1> {{ displayTitle }} </h1>
      <p> {{ count }} </p>
      <button v-on:click="incrementCount"> Increment Count</button>
      <div>
        <label for="incrementAmount"> Increment by : </label>
        <input type="number"
        v-model="incrementAmount" />
      </div>
      <hr />
      <p v-if= "message.length%2 === 0"> Even: {{ message.toUpperCase() }} </p>
      <p v-else> Odd: {{ message }} </p>
      <ul  v-for="(item, index) in listOfNumbers" :key="'item-${index}'">
        <li> {{ item.id   }}</li>
        <ul  v-for="(number, index) in item.list" :key="'number-${index}'">
        <li> {{ number  }}</li>
      </ul>
      </ul>
      
      
</template>


