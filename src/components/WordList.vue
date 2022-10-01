<script setup>
import { ref } from 'vue';
        
const items = ref([]);

const word = ref();

const addItem = () => {
	items.value.push(word.value);
	word.value = '';
}

const removeItem = (index) => {
	items.value.splice(index, 1);
}
</script>

<template>
	<div class="container">
		<div class="input-group">
			<input type="text" class="input-group__box" v-model="word">
			<button class="input-group__button" @click="addItem()">追加</button>
		</div>
		<ul class="word-list">
			<li v-for='(item, index) in items' :key='index' class="word-list__item">
				<button class="word-list__button" @click="removeItem(index)">X</button>
				<span class="word-list__txt">{{ item }}</span>
			</li>
		</ul>
	</div>
</template>

<style scoped>
.container {
	padding-top: 30px;
	width: 100%;
}

.input-group {
	margin: 0 auto;
	max-width: 300px;
	justify-content: space-between;
	display: flex;
}

.input-group__box {
	height: 30px;
	width: 80%;
	border-color: navy;
}

.input-group__button {
	color: white;
	background-color: navy;
	border-color: navy;
}

.word-list {
	margin: 0 auto;
	max-width: 300px;
	list-style: none;
	padding-top: 40px;
	padding-inline-start: 0;
}

.word-list__item {
	border-color: navy;
	border: 1px solid;
	margin-top: 10px;
}

.word-list__button {
	color: white;
	background-color: navy;
	border-color: navy;
	height: 50px;
	width: 50px;
}

.word-list__txt {
	padding-left:20px;
}
</style>