<template>
  <div class="hello">
    <h1>Hello Firestore!</h1>    
    <h2>My Name is {{name}}</h2>
    The number of the day is: {{ number }}

    <button v-on:click="number++">Increase me!</button>
    <ul>
      <li v-for="piece in compositions" :key="piece.Author">{{ piece.Title}}</li>
    </ul>
   <h3>The Counter's Length is {{ counter.length }} </h3>
   <button v-on:click="addDoc">Add item to counter</button>
  </div>
</template>

<script>
import { db } from '../db'
export default {
  name: 'HelloFirestore',
  data: () => {
    return {
      name: 'Nick',
      number: 42,
      compositions: [],
      counter: []
    }
  },
methods: {
  addDoc: function() {
    db.collection('Counter').add({
time: new Date()})
          }
         },
  firestore: {
    compositions: db.collection('compositions').where("Artist", "==", "Bach"),
    counter: db.collection('Counter')
             } 
}
</script>




