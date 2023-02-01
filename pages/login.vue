<template>
  <user-form-card>
    <template
      #user-form-card-content
    >
      <v-form
        ref="v-form"
        v-model="isValid"
      >
        <user-form-email
          :email.sync="params.user.email"
        />
        <user-form-password
          :password.sync="params.user.password"
        />
        <v-card-actions>
          <nuxt-link
            to="#"
            class="body-2 text-decoration-none"
          >
            パスワードを忘れた場合
          </nuxt-link>
        </v-card-actions>
        <v-cart-text
          class="px-0"
        >
          <v-btn
            :disabled="!isValid || loading"
            :loading="loading"
            block
            color="appblue"
            class="white--text"
            @click="login"
          >
            ログインする
          </v-btn>
        </v-cart-text>
      </v-form>
    </template>
  </user-form-card>
</template>

<script>
export default {
  layout: 'beforeLogin',
  data ({ $store }) {
    return {
      isValid: false,
      loading: false,
      params: { user: { email: '', password: '' } },
      redirectPath: $store.state.loggedIn.redirectPath
    }
  },
  methods: {
    login () {
      this.loading = true
      this.$router.push(this.redirectPath)
    }
  }
}
</script>
