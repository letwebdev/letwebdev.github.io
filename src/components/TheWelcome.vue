<script setup lang="ts">
	"use strict"
import { ref } from 'vue'
import { onMounted } from 'vue'

onMounted(() => {
  // component is now mounted.
  })

const countOfLike = ref(0)
countOfLike.value=JSON.parse(localStorage.getItem("countOfLike") ?? '0')
const color = ref('green')
function toggleColor() {
  color.value = color.value === 'green' ? 'orange' : 'green'
  }
function like() {
	countOfLike.value++
	if (Math.random()>0.8) {
	countOfLike.value++
	toggleColor()
	}
}
function store(){
  localStorage.setItem("countOfLike", JSON.stringify(countOfLike.value));
}
</script>

<template>
  <WelcomeItem>
    <template #icon>
    </template>
    <template #heading>Link</template>
	<br>
	<center class=links>
	<button @click="like() ;store()" :style="{ color }" >👍like: {{ countOfLike }}</button><br>
	<br>
	<a href="https://github.com/letwebdev" target="_blank" rel="noopener">GitHub profile</a>
	</center>
  </WelcomeItem>
</template>
<style scoped>
button{
	
}
.links {
	font-size: 2.5em;
}
button {
	font-size: 1em;
}
</style>
