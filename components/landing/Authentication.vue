<template>
  <div class="loginForm-holder">
    <div>{{ this.titleText }}</div>
    <form class="form row">
      <div class="col-md-12 col-lg-6 form-group">
        <input class="input white" v-model="email" type="email" placeholder="username or email address" />
        <input class="input white" v-model="password" type="password" placeholder="password" />
        <div v-show="this.authError !== ''" class="border-0 alert alert-danger alert-dismissible fade show" role="alert">
          <button @click="onDisposeErrorAlert" type="button" class="close" data-dismiss="alert" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
          <strong>:( </strong> {{ this.errorText }}
        </div>
      </div>

      <div class="buttons-holder col-md-12">
        <button @click="onAction" class="button button-lp-primary">{{ this.actionButtonText }}</button>
        <span class="or-text">OR</span>
        <div class="anonymous-login">
          <nuxt-link class="button button-lp-secondary" to="pomodoro" tag="button">START WITHOUT REGISTRATION</nuxt-link>
          <div class="anonymous-text">This version will not allow you to personalise your profile or add new workouts</div>
        </div>
      </div>
    </form>
    <div class="form-changer col-md-12 col-lg-6">
      <button @click="onSwitch" class="button button-lp-primary-faded">{{ this.switchButtonText }}</button>
    </div>
  </div>
</template>

<script>
  import {mapActions, mapGetters} from 'vuex'

  let TITLE_TEXT = {
    LOGIN: 'Already a member? Log in here!',
    SIGNUP: 'Don\'t have an account? Sign up here!'
  }
  let ACTION_BUTTON_TEXT = {
    LOGIN: 'LOGIN',
    SIGNUP: 'SIGN UP'
  }
  export default {
    data () {
      return {
        isLogin: true,
        email: '',
        password: ''
      }
    },
    computed: {
      ...mapGetters(['authError']),
      titleText () {
        return this.isLogin ? TITLE_TEXT.LOGIN : TITLE_TEXT.SIGNUP
      },
      switchButtonText () {
        return this.isLogin ? TITLE_TEXT.SIGNUP : TITLE_TEXT.LOGIN
      },
      actionButtonText () {
        return this.isLogin ? ACTION_BUTTON_TEXT.LOGIN : ACTION_BUTTON_TEXT.SIGNUP
      },
      errorText () {
        return this.isLogin ? 'LOGIN: ' + this.authError : 'SIGNUP: ' + this.authError
      }
    },
    methods: {
      ...mapActions(['createUser', 'authenticate', 'authenticateAnonymous', 'resetAuthError']),
      onSwitch () {
        this.resetAuthError()
        this.isLogin = !this.isLogin
      },
      onAction (ev) {
        ev.preventDefault()
        ev.stopPropagation()
        let method = this.isLogin ? this.authenticate : this.createUser
        method({email: this.email, password: this.password})
      },
      onDisposeErrorAlert (ev) {
        this.resetAuthError()
        ev.stopPropagation()
      }
    }
  }
</script>

<style lang="scss">
  @import "../../assets/styles/base/colors";
  @import "../../assets/styles/base/variables";
  @import "../../assets/styles/base/fontSizes";
  @import "../../assets/styles/vendors/flex";
  @import "../../assets/styles/vendors/bootstrap/functions";
  @import "../../assets/styles/vendors/bootstrap/variables";
  @import "../../assets/styles/vendors/bootstrap/mixins";
  @import "../../assets/styles/utils/module";
  .loginForm-holder {
    margin-top: 100px;
  }
  .form-group {
    padding-right: 0;
  }
  .form-changer {
    padding: 50px 0 20px;
    border-top: 2px dotted $color-white;
  }
  .input {
    margin-bottom: 30px;
  }
  .buttons-holder {
    @extend .center-content;
    @include justify-content(space-between);

    @include media-breakpoint-down(md) {
      @include justify-content(center);
      @include flex-direction(column);
    }
    .button-lp-primary {
      width: 50%;

      @include media-breakpoint-down(md) {
        width: 100%;
      }
    }
    .or-text {
      font-size: $font-size-medium;
      font-weight: bold;

      @include media-breakpoint-down(md) {
        margin-top: 20px;
        margin-bottom: 20px;
      }
    }
    .anonymous-login {
      position: relative;
      width: 40%;

      @include media-breakpoint-down(md) {
        width: 100%;
      }
    }
    .button-lp-secondary {
      width: 100%;
      font-size: $font-size-small;
    }
    .anonymous-text {
      position: absolute;
      font-weight: lighter;
      margin-top: 20px;

      @include media-breakpoint-down(md) {
        position: relative;
      }
    }
  }
  .button-lp-primary-faded {
    text-transform: none;
    font-weight: normal;
  }
  .border-0 {
    border-radius: 0!important;
  }

</style>
