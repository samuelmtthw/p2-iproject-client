<template>
  <section id="AboutPage">
    <div class="row my-5 py-5" data-aos="fade-up" data-aos-duration="600">
      <div class="col-6 d-flex justify-content-center">
        <img src="/assets/profpic.png" alt="">
      </div>
      <div class="col-6 d-flex flex-column justify-content-center">
        <h1>hello.</h1>
        <p>
          My name is <strong>Samuel Matthew</strong>. <br>
          I'm 21 years old and I'm from Indonesia 🇮🇩 <br>
          I like to build stuff, and one of them is custom mechanical keyboard. <br>
          I do offer keyboard build service (for Indonesia only) <br>
          For further information about the keyboard build service, please click <router-link to="/order">here</router-link>.<br>
        </p>
      </div>
    </div>
    <div class="clicker row mt-5 py-5" data-aos="fade-up" data-aos-duration="600" data-aos-delay="300">
      <a href="#youtube">
        <div class="d-flex flex-column">
          <h4 class="d-inline-block text-center">check out my youtube channel!</h4>
          <i class="fas fa-chevron-down text-center d-block"></i>
        </div>
      </a>
    </div>
    <a name="youtube"></a>
    <div class="row py-5 mb-5 d-flex flex-wrap justify-content-center">
      <iframe class="mb-4" :src="video" frameborder="0" v-for="(video, idx) in videos" :key="idx" data-aos="fade-up" data-aos-duration="600"></iframe>
    </div>
  </section>
</template>

<script>
import { alertError } from '@/apis/swal.js'
export default {
  name: 'AboutPage',
  data: function () {
    return {
      videos: []
    }
  },
  methods: {
    fetchVideos () {
      this.$store.dispatch('fetchVideos')
        .then((data) => {
          this.videos = data.videoEmbeds
        }).catch((err) => {
          alertError(err.message)
        })
    }
  },
  created () {
    this.fetchVideos()
  }
}
</script>

<style>

  #AboutPage .row1{
    height: 100%;
  }

  #AboutPage img {
    width: 350px;
    border-radius: 50em;
  }

  #AboutPage strong {
    font-weight: 600;
  }

  #AboutPage a {
    color: black;
    font-weight: 600;
    text-decoration: underline;
  }

  #AboutPage .clicker a{
    text-decoration: none;
  }

  #AboutPage i {
    font-size: 2em;
    color: #26466a;
  }

  #AboutPage iframe {
    width: 505px;
    height: 280px;
  }
</style>
