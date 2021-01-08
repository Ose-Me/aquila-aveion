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
  * {
  background: transparent;
  padding: 0;
  margin: 0;
  border: 0;
  outline: none;
  text-decoration: none;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

body {
  position: relative;
  margin: 0;
  font-family: "Roboto", sans-serif;
  font-size: 14px;
  line-height: 1.5;
  letter-spacing: 7px;
  color: #fff;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#home-container {
  position: relative;

  .background {
    display: flex;
    width: 100vw;
    min-height: 100vh;

    .left {
      background-color: #bd0f4d;
      width: 50%;
    }

    .right {
      background-color: #cb2964;
      width: 50%;
    }
  }

  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;

    .left {
      display: flex;
      justify-content: flex-end;
      width: 50%;
    }

    .right {
      width: 50%;
    }

    h1 {
      padding: 1rem;
      font-size: 2.2rem;
      font-weight: 100;
    }
  }

  .avatar {
    width: 50px;
    height: auto;
  }

  .nav {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding-bottom: 1.5rem;

    a {
      font-size: 1rem;
      font-weight: 300;
      text-decoration: none;
      color: #fff;
      padding: 0 2rem;
      z-index: 5;

      &:hover {
        color: #1cc253;
      }
    }
  }

  .nav-left {
    padding-right: 1.5rem;
  }

  .nav-right {
    padding-left: 1.5rem;
  }

  .girl-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 1;

    .girl {
      max-width: 400px;

      img {
        width: 100%;
        height: auto;
        box-shadow: 0px 0px 60px rgba(123, 44, 72, 0.9);
      }
    }
  }

  .social {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: center;
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;

    a {
      margin: 0.5rem 1.5rem 0.5rem 0;

      img:hover {
        transform: scale(1.1, 1.1);
      }
    }
  }
}

@media only screen and (max-width: 1024px) {
  #home-container .nav a {
    font-size: 0.9rem;
    letter-spacing: 5px;
    padding: 0 1rem;
    padding-bottom: 0.3rem;
  }

  .girl {
    width: 300px;
  }
}

@media only screen and (max-width: 425px) {
  .right,
  .left {
    display: flex;
    flex-direction: column;
  }

  .left {
    align-items: flex-end;
  }

  .girl {
    width: 250px;
  }

  .social a img {
    width: 24px;
  }

  #home-container .container h1 {
    font-size: 1.2rem;
    padding: 0.5rem;
    padding-top: 2.5rem;
  }
}

@media only screen and (max-width: 320px) {
  #home-container .social a {
    margin: 0.5rem;
  }

  .girl {
    width: 230px;
  }
}

</style>
