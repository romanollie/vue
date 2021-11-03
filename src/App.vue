/* eslint-disable vue/require-v-for-key */
<template>
  <div id="app">
    <div class="page">
        <div class="page__main main">
            <!-- HEADER -->
            <header class="main__header header">
                <div class="logo">
                    <img class="logo__img" src="./images/mainpage/logo.svg"
                    width="215px" height="35px" alt="Kolesa Group Logo">
                </div>
                <div class="header__activebar">
                    <Search></Search>
                    <User></User>
                </div>
            </header>
            <div class="main__showcase">
                <Navigation></Navigation>
                <!-- SECTION -->
                <section class="section">
                    <div class="section__banner banner">
                        <img class="banner_img" src="./images/mainpage/banner.svg"
                        width="1040px" height="335px" alt="banner">
                    </div>
                    <Hotbuttons></Hotbuttons>
                    <div class="section__radiobuttons radiobuttons">
                        <input @click="showAll" class="radiobuttons__input js__input--all"
                        type="radio" name="category" id="all-items">
                        <label class="radiobuttons__label" for="all-items">
                          Все товары
                        </label>
                        <input @click="showClothes" class="radiobuttons__input js__input--clothes"
                        type="radio" name="category" id="clothes">
                        <label class="radiobuttons__label" for="clothes">
                          Одежда
                        </label>
                        <input @click="showAccessories" class="radiobuttons__input
                        js__input--accessories"
                        type="radio" name="category" id="accessories">
                        <label class="radiobuttons__label"
                        for="accessories">
                          Аксессуары
                        </label>
                    </div>
                    <div class="section__catalog catalog js__catalog" >
                      <div v-show="clothesShown" v-for="item in clothesInfo" :key="item.id"
                      class="catalog__card card js__card" :class="item.id">
                        <img class="card__img" :src="item.mainImage"
                        :alt="item.description"
                        width="330px" height="330px">
                        <p class="card__points">{{ item.price }} баллов</p>
                        <p class="card__description">{{ item.title }}</p>
                        <p class="card__sizes"> {{
                          item.sizes && item.sizes.length ? `Размеры ${String(item.sizes)}` : ''
                          }}</p>
                        <div class="card__hidden">
                            <button @click="openCard(item)" class="card__button">Заказать</button>
                        </div>
                      </div>
                      <div v-show="accessoriesShown" v-for="item in accessoriesInfo" :key="item.id"
                      class="catalog__card card js__card" :class="item.id">
                        <img class="card__img" :src="item.mainImage"
                        :alt="item.description"
                        width="330px" height="330px">
                        <p class="card__points">{{ item.price }} баллов</p>
                        <p class="card__description">{{ item.title }}</p>
                        <p class="card__sizes">Размеры {{
                          item.sizes && item.sizes.length ? `Размеры ${String(item.sizes)}` : ''
                          }}</p>
                        <div class="card__hidden">
                            <button @click="openCard(item)" class="card__button">Заказать</button>
                        </div>
                      </div>
                    </div>
                </section>
            </div>
        </div>
        <footer class="page__footer footer">
            <div class="footer__content">
                <div class="footer__social social">
                    <p class="social__copy">&copy; Kolesa Group</p>
                    <div class="social__networks networks">
                        <a class="networks__link" href="#"><img class="networks__img"
                        src="./images/mainpage/instagram.svg"
                        width="18px" height="18px" alt="instagram logo"></a>
                        <a class="networks__link" href="#"><img class="networks__img"
                        src="./images/mainpage/youtube.svg"
                        width="18px" height="13px" alt="youtube logo"></a>
                        <a class="networks__link" href="#"><img class="networks__img"
                        src="./images/mainpage/vk.svg"
                        width="18px" height="11px" alt="vk logo"></a>
                    </div>
                </div>
                <div class="footer__feedback feedback">
                    <div class="feedback__description">
                        <p class="feedback__text">Есть идеи что улучшить?</p>
                        <p class="feedback__text">Не знаешь с кем решить проблему?</p>
                    </div>
                    <button class="feedback__button">Написать</button>
                </div>
            </div>
        </footer>
    </div>
    <Modal :data="modalData" :modalOpen="modalShown" @close="closeModal" @order="setScore"></Modal>
  </div>
</template>

<script>
import axios from './axios';
import Hotbuttons from './components/Hotbuttons.vue';
import Modal from './components/Modal.vue';
import Navigation from './components/Navigation.vue';
import Search from './components/Search.vue';
import User from './components/User.vue';

export default {
  name: 'App',
  components: {
    Modal,
    Search,
    User,
    Navigation,
    Hotbuttons,
  },
  data() {
    return {
      modalData: {},
      score: 500,
      clothesInfo: null,
      accessoriesInfo: null,
      userInfo: null,
      modalShown: false,
      clothesShown: true,
      accessoriesShown: true,
    };
  },
  methods: {
    openCard(data) {
      this.openModal();
      this.modalData = data;
    },
    openModal() {
      this.modalShown = true;
    },
    closeModal() {
      this.modalShown = false;
    },
    showAll() {
      this.clothesShown = true;
      this.accessoriesShown = true;
    },
    showClothes() {
      this.clothesShown = true;
      this.accessoriesShown = false;
    },
    showAccessories() {
      this.clothesShown = false;
      this.accessoriesShown = true;
    },
    setScore(price) {
      this.closeModal();
      this.score -= price;
    },
  },
  mounted() {
    axios.get('templates/-_RLsEGjof6i/data')
      .then((response) => {
        this.clothesInfo = response.data;
        console.log(this.clothesInfo);
      });
    axios.get('templates/q3OPxRyEcPvP/data')
      .then((response) => {
        this.accessoriesInfo = response.data;
      });
    axios.get('templates/7ZW3y5GAuIge/data')
      .then((response) => {
        this.userInfo = response.data;
      });
  },
};
</script>

<style lang="scss">
@import './scss/style.scss';
</style>
