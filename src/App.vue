<template>
  <div class="pageContainer">
    <section class="personInfo">
      <div class="personInfo__photo">
        <img alt="avatar"
             class="avatar_full"
             src="./img/avatar.png"
        >
      </div>
      <div class="personInfo__text">
        <div class="personInfo__header">
          <h3 class="personInfo__name">Вероника Ростова</h3>
          <p class="personInfo__profession">Менеджер по продажам</p>
          <p class="personInfo__title">Подберу для вас самые лучшие предложения. Мои услуги абсолютно бесплатны.</p>
        </div>
        <div class="personInfo__services">
          <p class="personInfo__services__header">Услуг</p>
          <div class="personInfo__table">
            <div class="personInfo__table__el">
              <p class="personInfo__table__name personInfo__table__name-main"
                 style="width: 219px;"
              >
                Ручное бронирование
              </p>
              <p class="personInfo__table__num">11</p>
            </div>
            <div class="personInfo__table__el">
              <p class="personInfo__table__name"
                 style="width: 54px;"
              >
                Пакетные туры
              </p>
              <p class="personInfo__table__num">3</p>
            </div>
            <div class="personInfo__table__el">
              <p class="personInfo__table__name"
                 style="width: 36px;"
              >
                Отели
              </p>
              <p class="personInfo__table__num">1</p>
            </div>
          </div>
          <div class="personInfo__services__total">
            <h3 class="personInfo__services__total__title">Всего</h3>
            <h3 class="personInfo__services__total__title">15</h3>
          </div>
        </div>
      </div>
    </section>
    <section class="reviews">
      <div class="reviews__header">
        <div class="reviews__header__block">
          <h3 class="reviews__title">Последние отзывы</h3>
          <a class="reviews__allBtn"
             href="#"
          >
            Все отзывы
          </a>
        </div>
        <div class="reviews__header__block">
          <div class="reviews__data">
            <img alt="likes"
                 class="reviews__data__img"
                 src="./img/like.png"
            >
            <p class="reviews__data__amount">131</p>
          </div>
          <div class="reviews__data">
            <img alt="likes"
                 class="reviews__data__img"
                 src="./img/comment.png"
            >
            <p class="reviews__data__amount">14</p>
          </div>
        </div>
      </div>
      <div v-for="(review, key) in reviews"
           :key="key"
           class="review"
      >
        <div class="review__header">
          <h4 class="review__name">{{ review.name }}</h4>
          <p class="review__date">{{ review.date }}</p>
        </div>
        <p class="review__text">{{ review.text }}</p>
      </div>
    </section>
    <section class="writeReview">
      <label for="inputReview"></label>
      <textarea id="inputReview"
                v-model="newReview"
                class="writeReview__input"
                @keydown.ctrl.enter.prevent="write"
      ></textarea>
      <button class="writeReview__button"
              @click="write"
      >
        Написать консультанту
      </button>
    </section>
  </div>
</template>

<script>
export default {
  name: "review",
  data: () => ({
    reviews: [
      {
        name: "Самуил",
        date: "13 октября 2011",
        text: "Привет, Верунь! ниче себе ты крутая. фотка класс!!!!"
      },
      {
        name: "Лилия Семёновна",
        date: "14 октября 2011",
        text: "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент, это и есть всемирно известный центр огранки алмазов и торговли бриллиантами?"
      },
      {
        name: "Лилия Семёновна",
        date: "14 октября 2011",
        text: "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?"
      }
    ],
    newReview: ""
  }),
  methods: {
    write() {
      if (this.newReview.trim() !== "") {
        const d = new Date();
        const date = d.getDate().toString() + "." + d.getMonth().toString() + "." + d.getFullYear().toString();
        this.reviews.push({
          name: "You",
          date: date.toString(),
          text: this.newReview.toString()
        })
        this.newReview = "";
      }
    }
  },
}


</script>

<style>
* {
  box-sizing: border-box;
}

h3 {
  font-size: 16px;
}

.pageContainer {
  min-width: 360px;
  max-width: 720px;
  margin: auto;
  font-family: Arial, sans-serif;
  font-size: 14px;
  padding: 15px;
  color: #333333;
}

.personInfo {
  display: flex;
  flex-wrap: nowrap;
  margin-bottom: 20px;
}

.personInfo__photo {
  margin: 0 15px 15px 0;
  z-index: 5;
}

.avatar_full {
  width: 125px;
}

.personInfo__name {
  margin: 0 0 10px 0;
}

.personInfo__profession {
  margin: 0 0 10px 0;
  color: #808080;
  font-size: 12px;
}

.personInfo__title {
  background-color: #FFFBC8;
  border: 1px solid #DADADA;
  border-radius: 5px;
  padding: 10px 10px 10px 20%;
  margin: 0 0 10px 0;
  width: 120%;
  float: right;
  text-align: right;
}

.personInfo__services__header {
  text-align: right;
  border-bottom: 1px solid #DADADA;
  margin: 0 0 15px 0;
  padding-bottom: 10px;
}

.personInfo__table {
  padding-bottom: 15px;
  border-bottom: 1px solid #DADADA;
  margin-bottom: 15px;
}

.personInfo__table__el {
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

.personInfo__table__name {
  margin: 0;
  padding: 5px;
  background-color: #ACE2F8;
  border-radius: 0 3px 3px 0;
}

.personInfo__table__name-main {
  background-color: #B1E19B;
}

.personInfo__table__num {
  margin: 0;
  padding: 5px;
}

.personInfo__services__total {
  display: flex;
  justify-content: space-between;
}

.personInfo__services__total__title {
  margin: 0;
}

.reviews__header {
  display: flex;
  justify-content: space-between;
}

.reviews__header__block {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.reviews__title {
  margin: 0 10px 0 0;
}

.reviews__allBtn {
  color: #005DA1;
}

.reviews__data {
  display: flex;
  align-items: center;
  margin-left: 20px;
}

.reviews__data__img {
  width: 15px;
  margin-right: 5px;
}

.reviews__data__amount {
  font-size: 12px;
  margin: 0;
}

.review__header {
  margin-bottom: 10px;
}

.review__name {
  display: inline;
  margin: 0 10px 0 0;
}

.review__date {
  margin: 0;
  display: inline;
  font-size: 12px;
  color: #808080;
}

.review__text {
  background-color: #F2FBFF;
  padding: 20px;
  border: 1px solid #C4CBCF;
  margin: 0 0 15px;
  box-shadow: 0 4px 10px rgba(128, 128, 128, 0.1);
}

.writeReview {
  background-color: #F2F2F2;
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.writeReview__input {
  width: 99%;
  border: 1px solid #000000;
  border-radius: 1px;
  height: 60px;
  margin-bottom: 20px;
}

.writeReview__button {
  padding: 15px 50px;
  background: #FDD639;
  border-radius: 23px;
  border: none;
  font-weight: bold;
  font-size: 16px;
  cursor: pointer;
}

@media (max-width: 425px) {
  .personInfo {
    flex-wrap: wrap;
  }

  .personInfo__title {
    text-align: left;
    float: left;
    width: 100%;
    padding: 10px;
  }

  .reviews__header {
    display: block;
  }

  .reviews__data {
    margin-left: 0;
    margin-right: 20px;
  }
}

</style>
