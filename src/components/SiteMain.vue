<template>
  <div class="container container2">
    <selectMusic @select-genre="setGenre" :genres="getGenres" />
    <div class="row">
      <div
        class="col-md-3 col_music"
        v-for="response in responses"
        :key="response.id"
      >
        <div class="music">
          <img :src="response.poster" :alt="response.genre" class="img" />
          <h3 class="title">{{ response.title }}</h3>
          <p class="author">{{ response.author }}</p>
          <p class="year">{{ response.year }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import selectMusic from "./selectMusic.vue";
export default {
  components: {
    selectMusic,
  },
  methods: {
    setGenre(genre) {
      this.genre = genre;
    },
  },
  computed: {
    getGenres() {
      let genres = [];
      this.responses.forEach((response) => {
        if (!genres.includes(response.genre)) {
          genres.push(response.genre);
        }
      });
      return genres;
    },
    filterDisks() {
      if (this.genres === "") {
        return this.responses;
      } else if (this.genres !== "") {
        return this.responses.filter(
          (responses) => responses.genre === this.genre
        );
      }
      return this.responses.filter(
        (responses) => responses.genre === this.genre
      );
    },
  },

  data() {
    return {
      responses: [],
      genres: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((r) => {
        console.log(r.data);
        this.responses = r.data.response;
        this.responses.forEach((album) => {
          console.log(album.genre);
          if (!this.genres.includes(album.genre)) {
            this.genres.push(album.genre);
          }
        });
      })
      .catch((e) => {
        console.log(e, "OPS");
      });
  },
};
</script>

<style lang="scss">
.container2 {
  background-color: #1e2d3b;
  height: 800px;

  .col_music {
    width: 220px;
  }
  .row {
    display: flex;
    justify-content: center;
    margin-left: px;
  }
  .music {
    background-color: #2e3a46;
    width: 180px;
    height: 280px;
    margin-top: 2rem;
  }
  .img {
    height: 130px;
    margin-left: 25px;
    margin-top: 25px;
  }
  .title {
    color: white;
    font-size: 18px;
    text-align: center;
    margin-top: 10px;
    padding: 10px;
  }
  .author {
    color: lightgray;
    text-align: center;
    filter: brightness(0.5);
  }
  .year {
    color: lightgrey;
    text-align: center;
    margin-top: -20px;
    filter: brightness(0.5);
  }
}
</style>