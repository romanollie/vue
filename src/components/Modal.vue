<template>
    <div v-if="modalOpen" @click.self="closeModal" class="pop pop__content js__pop">
        <div class="modal js__modal">
            <div class="modal__images">
                <div class="main-image">
                    <img class='js__modal-img' :src="data.mainImage" alt="cool shirt"
                    width="330px" height="330px">
                </div>
                <div class="options">
                    <div class="option1">
                        <img src="../images/modal/option1.svg" alt="cool shirt 1"
                        width="50px" height="50px">
                    </div>
                    <div class="option2 active">
                        <img src="../images/modal/option2.svg" alt="cool shirt 2"
                        width="50px" height="50px">
                    </div>
                    <div class="option3">
                        <img src="../images/modal/option3.svg" alt="cool shirt 3"
                        width="50px" height="50px">
                    </div>
                </div>
            </div>
            <div class="modal__description">
                <h3 class="title">
                    {{ data.title }}
                </h3>
                <div class="showcase">
                    <div class="showcase-left">
                        <p class="price">
                            {{ data.price }}
                        </p>
                        <button @click="order" class="button" type="button">
                            Заказать
                        </button>
                    </div>
                    <div class="balance">
                        <div class="current-balance">
                            <p class="your-balance">Твой баланс:</p>
                            <p>3 945 баллов</p>
                        </div>
                        <div class="bags">
                            <img src="../images/modal/bags.png" alt="">
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
                    <p class="modal__dsc">{{ data.description }}</p>
                </div>
                <div class="choose-size">
                    <h4 class="choose-title">Как выбрать размер:</h4>
                    <p>Написать дяде Рику для уточнения.</p>
                </div>
            </div>
            <div @click="closeModal" class="modal__close js__close-modal">
                <img src="../images/modal/close.png" alt="" width="24px" height="24px">
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    modalOpen: Boolean,
    data: Object,
  },
  data() {
    return {
      modalShown: false,
    };
  },
  methods: {
    closeModal() {
      this.$emit('close');
    },
  },
  order() {
    this.$emit('order', this.data.price);
  },
};
</script>

<style lang="scss">

</style>
