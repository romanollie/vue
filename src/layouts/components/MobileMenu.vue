<template>
  <div class="cascade__menu">
    <div class="cascade__menu-wrapper">
      <div class="cascade__menu-top">
        <div class="cascade__menu-logo">
          <a class="cascade__menu-logo__link" href="#"
            ><img
              class="cascade__menu-img"
              src="@/assets/images/header_logo.svg"
              alt="Логотип"
          /></a>
        </div>
        <a class="cascade__menu-user">
          <img
            class="cascade__menu-ava"
            src="@/assets/images/user.png"
            alt="Аватарка"
          />
          <div class="cascade__menu-name">
            Тимми <br />
              Тернер
          </div>
        </a>
      </div>
      <nav class="cascade__menu-bottom">
        <ul class="cascade__menu-list">
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">Оргсхема</a>
          </li>
          <li class="cascade__menu-item">
            <a
              class="cascade__menu-link cascade__menu-link--active"
              href="№"
              >Kolesa Team</a
            >
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№"
              >Kolesa <span>Shop</span></a
            >
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">Картина компании</a>
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">Новости</a>
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">Education</a>
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">Guidelines</a>
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">Библиотека</a>
          </li>
          <li class="cascade__menu-item">
            <a class="cascade__menu-link" href="№">FAQ</a>
          </li>
        </ul>
        <a class="cascade__menu-exit" href="#">Выйти из профиля</a>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MobileMenu',
};
</script>
