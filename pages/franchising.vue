<template>
  <div class="container">
    <nav class="pages-navigation" ref="mainNavigation">
      <ul class="navigation-list">
        <li @click="getScrollToElement($refs.advantages)">Про франчайзинг</li>
        <li @click="getScrollToElement($refs.franchisingGet)">Что Вы получите</li>
      </ul>
    </nav>
    <div class="franchising-banner mt-3">
      <div class="banner-wrapper mw-500 tac">
        <h2 class="mb-1">Задумываетесь о франшизе?</h2>
        <p class="mb-2">Хотите расширить свой бизнес в сфере общественного питания? Франчайзинг Ланч Маркет — это отличный способ
          быстро запустить доставку корпоративных обедов на базе вашего предприятия.</p>
        <el-button type="danger">Оформить заявку</el-button>
      </div>
    </div>
    <div class="franchising-advantages mw-800 tac" ref="advantages">
      <h2 class="mb-1">В чем преимущество франчайзинга</h2>
      <p class="mb-1">Мы ищем надежных партнеров, которые разделяют нашу страсть к совершенствованию и стремлению к лучшему
        сервису.</p>
      <p class="mb-1">Используя многолетний опыт Ланч Маркета, вы сможете значительно увеличить оборот вашего бизнеса, снизить
        зависимость от сезонных, кадровых и других негативных факторов.</p>
    </div>
    <div class="franchising-get" ref="franchisingGet">
      <h2 class="tac mb-1">Что Вы получите</h2>
      <div class="get-list mw-800">
        <div class="get-list__item">
          <h3>01</h3>
          <p>Право на использование товарного знака Ланч Маркет</p>
        </div>
        <div class="get-list__item">
          <h3>02</h3>
          <p>Возможность получать новых клиентов через наш лендинг</p>
        </div>
        <div class="get-list__item">
          <h3>03</h3>
          <p>Полноценный бэк-офис для администрирования заказов</p>
        </div>
        <div class="get-list__item">
          <h3>04</h3>
          <p>Бренд-бук с маркетинговыми материалами</p>
        </div>
        <div class="get-list__item">
          <h3>05</h3>
          <p>Индивидуальный заказ клиента через личный кабинет на сайте или через мобильное приложение</p>
        </div>
        <div class="get-list__item">
          <h3>06</h3>
          <p>Доступ к банку тех-карт и фотографий блюд</p>
        </div>
        <div class="get-list__item">
          <h3>07</h3>
          <p>Различные формы оплаты (картой на сайте, курьеру или банковским переводом)</p>
        </div>
        <div class="get-list__item">
          <h3>08</h3>
          <p>Полный контроль за тратами со стороны офис-менеджера компании-клиента</p>
        </div>
        <div class="get-list__item">
          <h3>09</h3>
          <p>Бонусная программа для клиентов</p>
        </div>
        <div class="get-list__item">
          <p>И многое другое</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "index",
  head: {
    titleTemplate: '%s - Франшиза'
  },
  mounted() {
    window.addEventListener('scroll', this.getScrollY)
  },
  destroyed() {
    window.removeEventListener('scroll', this.getScrollY)
  },
  methods: {
    getScrollToElement(element) {
      element.scrollIntoView({behavior: 'smooth', block: 'center'})
    },
    getScrollY() {
      if (window.scrollY > 40) {
        this.$refs.mainNavigation.classList.add('active')
      } else {
        this.$refs.mainNavigation.classList.remove('active')
      }
    },
  },
}
</script>

<style lang="scss">
@import "assets/css/variables";

.franchising-banner {
  background: url("../../assets/images/franchising-banner.jpg") no-repeat center top / cover;
  padding: 2rem;
  .banner-wrapper {
    background-color: white;
    width: 90%;
    margin: 0 auto;
    padding: 2rem;
  }
}

.franchising-advantages {
  margin: 2rem auto;
  padding: 2rem;
  @media screen and (max-width: 768px) {
    padding: 1rem;
  }
}

.franchising-get {
  background-color: $infoGray;
  padding: 3rem;
  .get-list {
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    .get-list__item {
      flex: 0 0 315px;
      background-color: white;
      border-radius: .5rem;
      margin: 1rem;
      padding: 1rem;
      text-align: center;
      box-shadow: 1px 1px 1px 1px $infoGray;
      h3 {
        color: $mainRed;
      }
    }
  }
}
</style>
