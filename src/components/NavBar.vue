<template>
  <header class="header">
    <h1>Food Fest Tickets</h1>
    <p>Book tickets for your favourite events</p>
    <button @click="$emit('toggle-favourites')">Favourites</button>
  </header>
  <div class="hero">
    <h2>Upcoming Event</h2>
    <p>Join us for an unforgettable culinary experience!</p>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
}

</script>

<style scoped>
.header{
  background: #7269e7;
  color:white;
  padding:5px;
  position: relative;
}

.header button{
  background:#2d9bcea2;
  color:white;
  border:none;
  padding:12px 20px;
  font-size:16px;
  cursor:pointer;
  position:absolute;
  right:15px;
  top:30px;
  border-radius:10px;
  
}

.header button:hover{
   background: #aaa9af;
}

.hero{
  height:80px;
  padding:5px;
  background: #ca6161;
  justify-content: center;
}

.hero h2, p{
  color:azure

}

</style>