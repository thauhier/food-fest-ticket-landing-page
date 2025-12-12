<template>
  <div id="app" class="landing-page">

<!--header-->
  <NavBar @toggle-favourites="toggleFavourites"/>
   

<!-- Main -->
  <TicketsCard
    v-for="ticket in tickets"
    :ticket="ticket"
    :key="ticket.type"
    :is-favourite="favourites.some(f => f.type === ticket.type)"
    @toggle-favourite="toggleFavourite"
  />
  <FavouriteList
    v-if="showFavourites"
    :favourites="favourites"
    @remove-favourite="removeFavourite"
  />
<!-- end of main -->

<!--footer-->
  <Footer/>
  </div>
</template>


<script setup>
import { ref } from 'vue';
import NavBar from './components/NavBar.vue';
import TicketsCard from './components/Tickets-Card.vue';
import Footer from './components/Footer.vue'; 
import FavouriteList from './components/FavouriteList.vue'
import tickets from './assets/data.js'

const favourites = ref([]);

const showFavourites = ref(false);
const toggleFavourites = () => {
  showFavourites.value = !showFavourites.value;
};


const toggleFavourite = (ticket) => {
  const idx = favourites.value.findIndex(t => t.type === ticket.type);
  if (idx === -1) {
    favourites.value.push(ticket);
  } else {
    favourites.value.splice(idx, 1);
  }
};

// remove items from favourites
const removeFavourite = (ticket) => {
  const idx = favourites.value.findIndex(t => t.type === ticket.type);
  if (idx !== -1) favourites.value.splice(idx, 1);
};
</script>


<style scoped>
.landing-page {
  font-family: Arial, sans-serif;
  text-align: center;
  color: #333;
  position:relative;
  background-color: beige;
}
</style>
