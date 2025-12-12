<template>
	<section class="favourites">
		<h2>Favourites</h2>
		<ul v-if="favourites && favourites.length">
			<li v-for="item in favourites" :key="item.type">
				<span>{{ item.type }}</span>
				<button @click="$emit('remove-favourite', item)">Remove</button>
			</li>
		</ul>
		<p v-else>No favourites yet.</p>
	</section>
</template>

<script setup>
const props = defineProps({
	favourites: { type: Array, default: () => [] }
});


</script>

<style scoped>
.favourites{
    position:absolute;
    right:0;
    top:102px;
    width:35%;
    background-color: rgb(218, 107, 107);
    height: 1000px;
    border: 2px solid white
}
.favourites h2{
    background-color: rgb(163, 157, 96);
    padding:15px;
    color:white;
    border-bottom: 2px solid black;
}

.favourites ul{
    list-style-type: none;
    padding:0;
    margin:0;
}

.favourites li{
    display:flex;
    justify-content: space-between;
    align-items: center;
    padding:10px 20px;
    border: 1px solid black;
    margin:5px;
}
button{
 border-radius: 15px;
  padding:5px;
  background-color: skyblue;
  border: none;
  margin: 5px;
}

</style>
