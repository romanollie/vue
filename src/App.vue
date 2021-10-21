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
                    <div class="searchbar">
                        <button class="searchbar__button">
                            <img src="./images/mainpage/search.svg"
                            width="18px" height="18px" alt="search image">
                        </button>
                        <input class="searchbar__input" type="text" placeholder="Поиск">
                    </div>
                    <a href="#" class="userbar">
                        <img class="userbar__img" src="./images/mainpage/user.svg"
                        width="44px" height="44px" alt="user image">
                        <span class="userbar__info">
                            <p class="userbar__name">Мортиджан</p>
                            <p class="userbar__points">300 баллов</p>
                        </span>
                    </a>
                </div>
            </header>
            <div class="main__showcase">
                <!-- NAVBAR -->
                <nav class="main__nav nav">
                    <ul class="nav__list">
                        <li class="nav__item"><a class="nav__link" href="#">Оргсхема</a></li>
                        <li class="nav__item">
                          <a class="nav__link" href="#">Kolesa
                            <span class="nav_link nav__link--bold">Team</span>
                          </a>
                        </li>
                        <li class="nav__item nav__item--active">
                          <a class="nav__link nav__link--bold" href="#">Kolesa Shop</a>
                        </li>
                        <li class="nav__item">
                          <a class="nav__link" href="#">Картина компании</a>
                        </li>
                        <li class="nav__item"><a class="nav__link" href="#">Новости</a></li>
                        <li class="nav__item"><a class="nav__link" href="#">Education</a></li>
                        <li class="nav__item"><a class="nav__link" href="#">Guidelines</a></li>
                        <li class="nav__item"><a class="nav__link" href="#">Библиотека</a></li>
                        <li class="nav__item"><a class="nav__link" href="#">FAQ</a></li>
                    </ul>
                </nav>
                <!-- SECTION -->
                <section class="section">
                    <div class="section__banner banner">
                        <img class="banner_img" src="./images/mainpage/banner.svg"
                        width="1040px" height="335px" alt="banner">
                    </div>
                    <div class="section__hotbuttons">
                        <button class="hotbutton hotbutton--green">
                            <img class="hotbutton__img" src="./images/mainpage/plus.svg"
                            width="48px" height="56px" alt="plus sign">
                            <span class="hotbutton__text">Получить баллы</span>
                        </button>
                        <button class="hotbutton hotbutton--yellow">
                            <img class="hotbutton__img" src="./images/mainpage/question.svg"
                            width="48px" height="56px" alt="question mark">
                            <span class="hotbutton__text">Как получить баллы</span>
                        </button>
                        <button class="hotbutton hotbutton--blue">
                            <img class="hotbutton__img" src="./images/mainpage/gift.svg"
                            width="48px" height="56px" alt="gift">
                            <span class="hotbutton__text">Подарить баллы</span>
                        </button>
                    </div>
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
                      <div v-show="clothesShown" v-for="item in clothes" :key="item"
                      class="catalog__card card js__card" :class="item.type">
                        <img class="card__img" :src="require(`./images/mainpage/${item.img}.svg`)"
                        :alt="item.alt"
                        width="330px" height="330px">
                        <p class="card__points">{{ item.price }} баллов</p>
                        <p class="card__description">{{ item.title }}</p>
                        <p class="card__sizes">Размеры S/M/L</p>
                        <div class="card__hidden">
                            <button @click="openModal" class="card__button">Заказать</button>
                        </div>
                      </div>
                      <div v-show="accessoriesShown" v-for="item in accessories" :key="item"
                      class="catalog__card card js__card" :class="item.type">
                        <img class="card__img" :src="require(`./images/mainpage/${item.img}.svg`)"
                        :alt="item.alt"
                        width="330px" height="330px">
                        <p class="card__points">{{ item.price }} баллов</p>
                        <p class="card__description">{{ item.title }}</p>
                        <p class="card__sizes">Размеры S/M/L</p>
                        <div class="card__hidden">
                            <button @click="openModal" class="card__button">Заказать</button>
                        </div>
                      </div>
                      <!-- <div v-for="item in clothes" :key="item" data-id="${id}"
                      class="catalog__card card js__card ${type}">
                          <img class="card__img" src="${img}"
                          width="330px" height="330px" alt="${alt}">
                          <p class="card__points">{{ this.price }} баллов</p>
                          <p class="card__description">${title}</p>
                          <p class="card__sizes">Размеры S/M/L</p>
                          <div class="card__hidden">
                              <button class="card__button">Заказать</button>
                          </div>
                      </div> -->
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
    <!-- MODAL -->
    <div v-show="modalShown" class="pop pop__content js__pop">
        <div class="modal js__modal">
            <div class="modal__images">
                <div class="main-image">
                    <img class='js__modal-img' src="./images/modal/image1.svg" alt="cool shirt"
                    width="330px" height="330px">
                </div>
                <div class="options">
                    <div class="option1">
                        <img src="./images/modal/option1.svg" alt="cool shirt 1"
                        width="50px" height="50px">
                    </div>
                    <div class="option2 active">
                        <img src="./images/modal/option2.svg" alt="cool shirt 2"
                        width="50px" height="50px">
                    </div>
                    <div class="option3">
                        <img src="./images/modal/option3.svg" alt="cool shirt 3"
                        width="50px" height="50px">
                    </div>
                </div>
            </div>
            <div class="modal__description">
                <h3 class="title">
                    Футболка "Эволюционируй или сдохни"
                </h3>
                <div class="showcase">
                    <div class="showcase-left">
                        <p class="price">
                            100 баллов
                        </p>
                        <button class="button" type="button">
                            Заказать
                        </button>
                    </div>
                    <div class="balance">
                        <div class="current-balance">
                            <p class="your-balance">Твой баланс:</p>
                            <p>3 945 баллов</p>
                        </div>
                        <div class="bags">
                            <img src="./images/modal/bags.png" alt="">
                        </div>
                    </div>
                </div>
                <p class="colors-title">
                    Цвета:
                </p>
                <div class="colors">
                    <input type="radio" name="color" id="blue">
                    <label class="options blue" for="blue">Синий</label>
                    <input type="radio" name="color" id="beige">
                    <label class="options beige" for="beige">Бежевый</label>
                    <input type="radio" name="color" id="gray">
                    <label class="options gray" for="gray">Серый</label>
                </div>
                <p class="sizes-title">
                    Размер:
                </p>
                <div class="sizes">
                    <input type="radio" name="size" id="s">
                    <label class="s" for="s">S</label>
                    <input type="radio" name="size" id="m">
                    <label class ="m" for="m">M</label>
                    <input type="radio" name="size" id="l">
                    <label class="l" for="l">L</label>
                </div>
                <div class="details">
                    <h4 class="details-title">Детали:</h4>
                    <p class="modal__dsc">Брендированная толстовка от Qazaq Republic.
                    Материал: Хлопок 80%, Вискоза 20%</p>
                </div>
                <div class="choose-size">
                    <h4 class="choose-title">Как выбрать размер:</h4>
                    <p>Написать дяде Рику для уточнения.</p>
                </div>
            </div>
            <div @click="closeModal" class="modal__close js__close-modal">
                <img src="./images/modal/close.png" alt="" width="24px" height="24px">
            </div>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      clothes: [
        {
          id: 0,
          title: 'Зеленая рубашка',
          price: 100,
          isNew: false,
          img: 'tshirt--green',
          alt: 'Зеленая рубашка',
          type: 'clothes',
        },
        {
          id: 1,
          title: 'Зеленый свитер',
          price: 300,
          isNew: false,
          img: 'sweater--green',
          alt: 'Зеленый свитер',
          type: 'clothes',
        },
        {
          id: 2,
          title: 'Белая рубашка',
          price: 110,
          isNew: false,
          img: 'tshirt--white',
          alt: 'Белая рубашка',
          type: 'clothes',
        },
        {
          id: 3,
          title: 'Белые джинсы',
          price: 220,
          isNew: false,
          img: 'trousers--white',
          alt: 'Белые джинсы',
          type: 'clothes',
        },
        {
          id: 4,
          title: 'Синие джинсы',
          price: 270,
          isNew: false,
          img: 'trousers--blue',
          alt: 'Синие джинсы',
          type: 'clothes',
        },
        {
          id: 5,
          title: 'Белый халат',
          price: 400,
          isNew: false,
          img: 'coat--white',
          alt: 'Белый халат',
          type: 'clothes',
        },
      ],
      accessories: [
        {
          id: 6,
          title: 'Бутылка для воды',
          price: 50,
          isNew: false,
          img: 'bottle',
          alt: 'Бутылка для воды',
          type: 'accessories',
        },
        {
          id: 7,
          title: 'Зеленая сумка',
          price: 450,
          isNew: false,
          img: 'bag--green',
          alt: 'Зеленая сумка',
          type: 'accessories',
        },
        {
          id: 8,
          title: 'Красный шарф',
          price: 140,
          isNew: false,
          img: 'scarf--red',
          alt: 'Красный шарф',
          type: 'accessories',
        },
        {
          id: 9,
          title: 'Белый шарф',
          price: 115,
          isNew: false,
          img: 'scarf--white',
          alt: 'Белый шарф',
          type: 'accessories',
        },
        {
          id: 10,
          title: 'Синяя сумка',
          price: 470,
          isNew: false,
          img: 'bag--blue',
          alt: 'Синяя сумка',
          type: 'accessories',
        },
        {
          id: 11,
          title: 'Наушники',
          price: 700,
          isNew: false,
          img: 'headphones',
          alt: 'Наушники',
          type: 'accessories',
        },
      ],
      modalShown: false,
      clothesShown: true,
      accessoriesShown: true,
    };
  },
  methods: {
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
  },
};
</script>

<style lang="scss">
@import './scss/style.scss';
</style>
