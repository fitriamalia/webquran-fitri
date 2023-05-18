<template>

  <div class="surah">
    <h1 class="title"><u>Baca Qur'an</u></h1>
    <li class="card" style="width: 30rem" v-for="item in listSurah">
      <h3 class="item1">{{ 'Surah ke - ' + item.id }} </h3>
      <h3 class="item2">{{ item.name_simple + ' (' + item.name_arabic + ')' + ' | ' +  item.revelation_place }}</h3>
      <h3 class="item3">{{ item.translated_name.name + ' - ' + item.verses_count + ' Ayat'}}</h3>
      <router-link :to="{name: 'surah', params: {id: item.id}}" class="btn btn-primary">Baca Surah</router-link> <hr>
    </li>

    <hr>

    <footer class="text-black text-center pb-5">
      <p>&copy; 2023 <a href="#" class="text-black fw-bold">Al-Qur'an</a> &middot; Created by Fitri Amalia</p>
    </footer>
  </div>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'

export default {

  data() {
    return {
      listSurah: ref([])
    }
  },

  mounted() {
    this.getListSurah()
  },

  methods: {
    getListSurah() {
      axios.get('https://api.quran.com/api/v4/chapters?language=id')
          .then((response) => {
            console.log(response)
            this.listSurah = response.data.chapters
          }).catch ((err) => {
        console.log(err)
      })
    }
  }
}

</script>

<style>

.surah {
  background-color: #76a973;
}

li {
  list-style: none;
  padding-left: 20pt;
  padding-top: 20pt;
}

.title {
  text-align: center;
  font-weight: bold;
  text-transform: uppercase;
  font-size: 40pt;
}

.card {
  display: inline-block;
  align-content: center;
  margin-left: 90px;
  margin-top: 20pt;
  background-color: #282828;
  -webkit-text-fill-color: white;
  text-align: center;
}

p {
  text-align: center;
}

.btn {
  font-size: 15pt;
  -webkit-text-fill-color: white;
  width: 100pt;
  background-color: #005400;
  border-color: #282828;
  margin-top: 5pt;
}

.text-black {
  font-size: 20pt;
}

.item1 {
  font-size: 18pt;
}

.item2 {
  font-size: 18pt;
  text-transform: capitalize;
}

.item3 {
  font-size: 18pt;
}

</style>