<!-- 
api url: https://newsapi.org/v2/everything? 


-->
<script setup>
import { computed, ref } from 'vue'

const query = ref('')
const date = ref()
const date2 = ref()
const current = new Date()
const api = ref('https://newsapi.org/v2/everything?')
const key = ref('')
const articles = ref([])
const sect = ref()

const formatedQuery = computed(() => {
  return query.value.split(' ').join('+')
})

const formatedList = computed(() => {
  return articles.value.length > 0 ? articles.value.filter((e) => e.title !== '[Removed]') : []
})

async function fetchData() {
  if (key.value === '' || key.value.length < 32) {
    sect.value.innerHTML = 'enter a valid api key'
    return 0
  }
  const rq = await fetch(
    `${api.value}q=${formatedQuery.value}&from=${date.value || `${current.getFullYear()}-${String(current.getMonth() + 1).padStart(2, '0')}-${String(current.getDate()).padStart(2, '0')}`}&to=${date.value || `${current.getFullYear()}-${String(current.getMonth() + 1).padStart(2, '0')}-${String(current.getDate()).padStart(2, '0')}`}&apiKey=${key.value}`
  )
  const data = await rq.json()
  if (data.articles[0] === undefined) {
    sect.value.innerHTML = 'no articles found'
  } else {
    data.articles.length = 10
    articles.value = data.articles
  }
  query.value = ''
}
</script>

<template>
  <main>
    <span>
      <label for="key">enter a valid api key</label>
      <input type="text" v-model="key" />
    </span>
    <span>
      <label for="search">search</label>
      <input type="search" name="search" id="" v-model="query" />
    </span>
    <span>
      <label for="from">from</label>
      <input type="date" name="from" id="" v-model="date" @change="console.log(date)" />
    </span>
    <span>
      <label for="to">to</label>
      <input type="date" name="to" id="" v-model="date2" @change="console.log(date2)" />
    </span>
    <button @click="fetchData">search</button>
  </main>
  <h1>
    Note: due to the app using the free version of the API you are only limited to look up articles
    that are at most a month old
  </h1>
  <section ref="sect">
    <div v-for="item in formatedList">
      <h1>{{ item.title }}</h1>
      <p>{{ item.description }}</p>
      <a :href="item.url" target="_blank">read the article</a>
    </div>
  </section>
</template>

<style scoped>
main {
  border-radius: var(--br-radius);

  padding: 15px;
  justify-self: center;
  width: fit-content;
  background-color: var(--bg-color);
  text-align: center;
  justify-content: center;
  display: grid;
}

input[type='date'] {
  justify-self: center;
  width: 80%;
}

span {
  justify-self: center;
  display: flex;
  justify-content: space-evenly;
}

section {
  justify-content: center;
  align-content: space-evenly;
  display: grid;
  gap: 12px;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(autofill, minman(250px, 1fr));
}

div {
  text-align: center;
  border-radius: var(--br-radius);
  background-color: var(--bg-color);
  color: var(--line-color);
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-size: 1rem;
}

a {
  text-decoration: none;
  transition-duration: 200ms;
}

a:hover {
  text-decoration: underline;
}

h1 {
  text-align: center;
  border-bottom: 3px dotted var(--line-color);
}
</style>
