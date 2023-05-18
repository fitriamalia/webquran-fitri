<template>
  <div class="ayat">
    <li class="ayatquran" v-for="(item, index) in ayatQuran">
      {{ item.verse_key }} <br>
      {{ item.text_uthmani }}
      <i><p class="artiquran" v-html="artiQuran[index].text"></p></i>
      <hr>
    </li>

    <footer class="text-black text-center pb-5">
      <p>&copy; 2023 <a href="#" class="text-black fw-bold">Al-Qur'an</a> &middot; Created by Fitri Amalia</p>
    </footer>
  </div>
</template>

<script>
import axios from 'axios';
import { ref } from 'vue';

export default {

  data() {
    return {
      ayatQuran: ref([]),
      artiQuran: ref([]),
      listSurah: ref([])
    }
  },

  mounted() {
    this.getAyatQuran()
    this.getArtiQuran()
  },

  methods: {
    getAyatQuran() {
      axios.get(`https://api.quran.com/api/v4/quran/verses/uthmani?chapter_number=${this.$route.params.id}`)
          .then ((response) => {
            console.log(response)
            this.ayatQuran = response.data.verses
          }).catch((err) => {
        console.log(err)
      })
    },

    getArtiQuran() {
      axios.get(`https://api.quran.com/api/v4/quran/translations/33?chapter_number=${this.$route.params.id}`)
          .then((respons) => {
            console.log(respons)
            this.artiQuran = respons.data.translations
          }).catch((err) => {
        console.log('error' + err)
      })
    }
  }
}

</script>

<style>

.ayat {
  text-align: right;
  padding-right: 30pt;
  padding-left: 30pt;
  font-family: sans-serif;
  background-color: #74a662;
  margin-top: 5pt;
}

.ayatquran  {
  text-align: right;
  font-size: 28pt;
  list-style: none;
}

.artiquran {
  text-align: left;
  font-size: 18pt;
  padding-top: 10pt;
}

.text-black {
  font-size: 15pt;
}

</style>