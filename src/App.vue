<template>
<div id="#app">
  <h1>Lugares que quiero visitar</h1>
  <PlaceForm @add-place="handleAddPlace"/>
  <ul>
    <li v-for="place in placeToVisit" :key="place">
      {{ place }}
      <button @click="removePlace(place)">Eliminar</button>
    </li>
  </ul>
</div>
</template>

<script>
import PlaceForm from './components/PlaceForm.vue';

export default {
  components:{
    PlaceForm
  },
  data(){
    return {
      placeToVisit: []
    };
  },

  methods:{
    handleAddPlace(place){
      if (place && !this.placeToVisit.includes(place)){
        this.placeToVisit.push(place);
      }
    },
    removePlace(place){
      this.placeToVisit = this.placeToVisit.filter(p => p !== place);
    }
  },
}

</script>