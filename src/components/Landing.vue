<template>
  <div id="home-container">
    <div class="background">
      <div class="left"></div>
      <div class="right"></div>
    </div>

    <div class="girl-container">
      <div class="container">
        <div class="left">
          <h1>{{ firstName }}</h1>
        </div>
        <div class="right">
          <h1>{{ lastName }}</h1>
        </div>
      </div>

      <div class="girl">
        <img src="../assets/images/girl.png" alt="" />
      </div>

        <div class="social">
          <a :href="'https://instagram.com/' + instagram" target="_blank">
            <img src="../assets/images/icons/instagram.png" alt="instagram" />
          </a>
          <a :href="'https://twitter.com/' + twitter" target="_blank">
            <img src="../assets/images/icons/twitter.png" alt="twitter" />
          </a>
          <a :href="'https://snapchat.com/' + snapchat" target="_blank">
            <img src="../assets/images/icons/snapchat.png" alt="snapchat" />
          </a>
          <a :href="'mailto:' + email" target="_blank">
            <img src="../assets/images/icons/email.png" alt="email" />
          </a>
        </div>

        <div class="nav">
          <div class="container">
          <div class="left">
            <a href="">HOME</a>
            <a href="">ABOUT</a>
          </div>
          <img
              src="../assets/images/icons/avatar.png"
              alt="avatar"
              class="avatar"
            />
          <div class="right">
            
            <a href="">GALLERY</a>
            <a href="">CONTACT</a>
          </div></div>
        </div>

    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import axios from "axios";
import "./landingPage/landing.scss";

@Component
export default class Landing extends Vue {
  firstName = "";
  lastName = "";
  name = "";
  instagram = "";
  twitter = "";
  snapchat = "";
  email = "";

  mounted() {
    axios.get("https://hirng-x2021.glitch.me/api").then((response: any) => {
      this.firstName = response.data.name.split(" ")[0];
      this.lastName = response.data.name.split(" ")[1];
      this.instagram = response.data.social_media.instagram;
      this.twitter = response.data.social_media.twitter;
      this.snapchat = response.data.social_media.snapchat;
      this.email = response.data.social_media.email;
      console.log(response.data, this.instagram);
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
