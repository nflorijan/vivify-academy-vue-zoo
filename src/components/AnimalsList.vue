<template>
  <div>
    <h2>Animals List</h2>
    <table>
      <tr>
        <th>Vrsta</th>
        <th>Ime</th>
        <th>Datum Rodjenja</th>
      </tr>
      <tr v-for="(animal, index) in animals" :key="index">
        <td>{{ animal.vrsta }}</td>
        <td>{{ animal.ime }}</td>
        <td>{{ animal.datumRodjenja ? animal.datumRodjenja: 'Nepoznat' }}</td>
        <button @click="deleteFromList(index)">Remove</button>
        <button @click="moveToTop(index)">Move to to top</button>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  name: 'AnimalsList',
  data () {
    return {
      animals: [
        {vrsta: 'Pas', ime: 'Zuca', datumRodjenja: new Date(2018, 11, 24)},
        {vrsta: 'Macka', ime: 'Lunja', datumRodjenja: new Date(2020, 12, 20)},
        {vrsta: 'Prase', ime: 'Joca', datumRodjenja: new Date(2020, 1, 21)},
        {vrsta: 'Papagaj', ime: 'Papi', datumRodjenja: null}
      ]
    }
  },
  methods: {
    deleteFromList(index) {
      this.animals.splice(index, 1);
    },
    moveToTop(index){
      const movedItem = this.animals.splice(index, 1);
      return this.animals.unshift(movedItem[0]);
    },
  }
}
</script>