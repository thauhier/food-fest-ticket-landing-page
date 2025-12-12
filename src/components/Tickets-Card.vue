<template>
<!-- features -->
    <section class="features">
      <div class="feature">

          <div v-if="!showFeatures" class="ticket-info">
            <h3>{{ticket.type}}</h3>
            <img :src="ticket.image" alt="ticket type">
            <p>{{ ticket.description }}</p>
            <p>Features: {{ ticket.features.length }}</p>
            <button :class="{ favourite: isFavourite }" @click="toggleFavourite">
              {{ buttonLabel }}
            </button>
            <button @click="toggleView">View</button>
          </div>

          <!-- Product Features -->
      <div v-else class="ticket-features">
        <h2>{{ ticket.type }} - Features</h2>
        <ul class="feature-list">
          <li v-for="feature in ticket.features" :key="feature">
            {{ feature }}
          </li>
        </ul>
        <button @click="toggleView">Back</button>
      </div>
      </div>
    </section>
</template>

<script setup>
import {ref} from 'vue'
import { computed } from 'vue';
const { ticket, isFavourite } = defineProps({
  ticket: Object,
  isFavourite: { type: Boolean, default: false }
});
const emit = defineEmits(['toggle-favourite']);

const buttonLabel = computed(() =>
  isFavourite ? 'Remove from favourites' : 'Add to favourites'
);

// favorite button function
const toggleFavourite = () => {
  emit('toggle-favourite', ticket);
};

const showFeatures = ref(false)

// view button funstion
function toggleView(){
  showFeatures.value =!showFeatures.value
}
</script>

 

<style scoped>

.features{
  display:flex;
  justify-content:center;
  gap:20px;
  padding:30px;
  flex-wrap:wrap;
}

.feature{
  background: rgb(163, 157, 96);
  border:1px solid #ddd;
  padding: 20px;
  width:70%;
  border-radius:8px;
  height:75vh
  
  
}

button{
  border-radius: 15px;
  padding:10px;
  background-color: skyblue;
  border: none;
  margin: 3px;
  margin-top: 0;
}

button:hover{
  background-color:aqua;
}

.feature-list{
  list-style: none;
}

img{
  width:100%;
  height:50vh
}

</style>