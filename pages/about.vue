<template>
  <div>
    <header-component></header-component>
    <div class="container min-full-height">
      <p class="lead">
        ProFitOro is a time management application that combines the <a target="_blank" href="https://en.wikipedia.org/wiki/Pomodoro_Technique">Pomodoro technique</a> with office workouts.
      </p>
      <p class="lead">
        <nuxt-link to="login">Click here to login </nuxt-link> or just <nuxt-link to="pomodoro">start using ProFitOro </nuxt-link>without registration.
      </p>
      <p class="lead">
        Every time your Pomodoro working interval ends, you will be presented with a small workout that you have to perform during the Pomodoro resting period.
      </p>
      <h4 class="title">There are some advantages to become a <nuxt-link to="login">registered user</nuxt-link>:</h4>
      <p>
        As a registered user you can <nuxt-link to="settings">configure</nuxt-link> your Pomodoro timing settings.
      </p>
      <p>
        You can also <nuxt-link to="workouts">manage</nuxt-link> workouts, choosing your favourite ones, rating them and even creating your own workouts that will be displayed to everybody!
      </p>
      <p>
        You can also <nuxt-link to="statistics">check your statistics</nuxt-link> along the time you use ProFitOro!
      </p>
      <h4 class="title">Book</h4>
      <p>
        This application has been developed as a part of the book <a target="_blank" href="https://www.packtpub.com/web-development/web-development-bootstrap-and-vuejs">"Web development using Vue.js, Bootstrap and Firebase"</a>. It is an <a
        href="https://github.com/chudaol/profitoro">open source project</a> licensed under the Apache License, Version 2.0.
      </p>
      <h4 class="title">Credits</h4>
      <p>Logo creation: <a href="mailto:car.marg@gmail.com">Carina</a></p>
      <p>Mockups by: <a href="https://github.com/Safure">Safi</a></p>
      <p>Design and illustrations: <a href="https://www.behance.net/MeegsyWeegsy">Vanessa</a></p>
      <p>Design implementation: <a href="https://github.com/fil090302">Filipe</a></p>
      <p>Functionality implementation using Vue, Bootstrap and Firebase: <a href="https://github.com/chudaol">Olga</a></p>
    </div>
    <footer-component></footer-component>
  </div>
</template>
<script>
  import { HeaderComponent, FooterComponent } from '~/components/common'

  export default {
    components: {
      HeaderComponent,
      FooterComponent
    }
  }
</script>
<style scoped lang="scss">
  @import "../assets/styles/vendors/bootstrap/functions";
  @import "../assets/styles/vendors/bootstrap/variables";
  @import "../assets/styles/vendors/bootstrap/mixins/breakpoints";

  .container {
    padding: 30px 15px;

    @include media-breakpoint-up(lg) {
      padding: 50px 15px;
      max-width: 800px;
    }
  }
  .title {
    margin: 30px 0 15px;
  }
</style>
