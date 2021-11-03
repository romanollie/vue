<template>
  <div class="header__right">
    <a class="header__user" href="#" target="_blank">
      <img class="header__ava" :src="userInfo.avatarUrl" alt="Пользователь" />
      <div class="header__user-info">
        <div class="header__username">{{ userInfo.name }}</div>
        <div class="header__userpoints">{{ userInfo.score }} баллов</div>
      </div>
    </a>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  name: 'User',
  computed: {
    ...mapState({
      userInfo: 'userInfo',
    }),
  },
  mounted() {
    this.fetchUser();
  },
  methods: {
    fetchUser() {
      this.$store.dispatch('fetchUserInfo');
    },
  },
};
</script>
