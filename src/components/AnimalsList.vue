<template>
  <div>
    <h2>Animals List</h2>
    <h4>Add Animal</h4>
    <form v-on:submit.prevent="addAnimal">
      <label>
        Vrsta:
      </label>
      <input type="text" v-model="novaVrsta">
      <label>
        Ime:
      </label>
      <input type="text" v-model="novoIme">
      <label>
        Datum Rodjenja:
      </label>
      <input type="date" v-model="noviDatumRodjenja">
      <label>Select sector</label>
      <select v-model="noviSektor">
        <option v-for="(sector, index) in sectors" :key="index">
          {{ sector }}
        </option>
      </select>
      <button>Add Animal</button>
    </form>
    <table>
      <tr>
        <th>Vrsta</th>
        <th>Ime</th>
        <th>Datum Rodjenja</th>
        <th>Sektor</th>
      </tr>
      <tr v-for="(animal, index) in animals" :key="index">
        <td>{{ animal.vrsta }}</td>
        <td>{{ animal.ime }}</td>
        <td>{{ animal.datumRodjenja ? animal.datumRodjenja: 'Nepoznat' }}</td>
        <td>{{ animal.sektor ? animal.sektor: 'Nepoznat' }}</td>
        <button @click="deleteFromList(index)">Remove</button>
        <button @click="moveToTop(index)">Move to to top</button>
      </tr>
    </table>

    <h2>Lista Sektora</h2>
    <table>
      <tr>
        <th>Sektor</th>
      </tr>
      <tr v-for="(sector, index) in sectors" :key="index">
        <td>{{ sector }}</td>
        <button @click="getAllAnimals(sector)">Vidi listu zivotinja</button>
      </tr>
    </table>
  </div>
</template>
<script>
import { format } from 'date-fns'

export default {
  name: 'AnimalsList',
  data () {
    return {
      novaVrsta: '',
      novoIme: '',
      noviDatumRodjenja: '',
      animals: [
        {vrsta: 'Koker spanijel', ime: 'Zuca', datumRodjenja: format(new Date(2018, 11, 24), 'MMM dd, yyyy'), sektor: 'Pas'},
        {vrsta: 'Rotvajer', ime: 'Arci', datumRodjenja: format(new Date(2020, 12, 24), 'MMM dd, yyyy'), sektor: 'Pas'},
        {vrsta: 'Sibirska sumska', ime: 'Lunja', datumRodjenja: format(new Date(2020, 12, 20), 'MMM dd, yyyy')},
        {vrsta: 'Anakonda', ime: 'Joca', datumRodjenja: format(new Date(2020, 1, 21), 'MMM dd, yyyy'), sektor: 'Zmija'},
        {vrsta: 'Papagaj', ime: 'Papi'}
      ],
      sectors: ['Ptica', 'Zmija', 'Pas', 'Macka'],
      sector: '',
      noviSektor: ''
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
    addAnimal() {
      this.animals.push({
        vrsta: this.novaVrsta,
        ime: this.novoIme,
        datumRodjenja: format(new Date(this.noviDatumRodjenja), 'MMM dd, yyyy'),
        sektor: this.noviSektor,
      })
    },
    getAllAnimals (sector) {
       const array = this.animals.filter(data => data.sektor === sector)
  
        console.log(array);
        
    }


  }
}
</script>