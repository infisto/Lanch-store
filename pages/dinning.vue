<template>
  <div class="container">
    <nav class="pages-navigation" ref="mainNavigation">
      <ul class="navigation-list">
        <li @click="scrollIntoElement($refs.reliability)">C нами надежно</li>
        <li @click="scrollIntoElement($refs.deals)">Предложения</li>
        <li @click="scrollIntoElement($refs.furshet)">Организуем фуршет</li>
      </ul>
    </nav>
    <div class="dinning-content mt-3">
      <div class="content-body">
        <h1 class="mb-1">Хотите столовую?</h1>
        <p class="mb-1">За годы работы мы создали десятки проектов по организации питания на производствах, в офисных центрах,
          учебных заведениях.</p>
        <p class="mb-2">Мы поможем подобрать оптимальный вариант для вашей компании и воплотить его в жизнь.</p>
        <el-button type="primary" plain>Пригласить нас</el-button>
      </div>
    </div>
    <div class="dinning-aside" ref="reliability">
      <div class="aside-text">
        <h2 class="mb-1">С нами надежно</h2>
        <p>Мы контролируем процесс на каждом этапе от проектирования до запуска столовой. Тщательная разработка проекта,
          всесторонний контроль качества и безопасности производства, привлечение к работе лучших профессиональных
          кадров — наши основные приоритеты.</p>
      </div>
      <div class="aside-certificate">
        <el-button type="danger" icon="el-icon-document-checked">Сертификат соответствия</el-button>
        <el-button type="danger" icon="el-icon-fork-spoon">Проект столовой</el-button>
      </div>
    </div>
    <div ref="deals">
      <h2 class="tac">Подберем вариант для любого бизнеса</h2>
      <el-tabs v-model="activeName">
        <el-tab-pane label="Линия раздачи" name="first">
          <picture>
            <img src="~/assets/images/liniya-razdachi.png" alt="liniya razdachi">
          </picture>
          <article>
            <h3>Линия раздачи</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab accusamus commodi, earum enim facere,
              inventore iure, labore laborum nisi obcaecati optio possimus praesentium ratione repudiandae veniam!
              Architecto aut blanditiis dicta, laboriosam maiores, minus necessitatibus praesentium, quam qui rem
              repudiandae temporibus ullam vel veritatis voluptatem. Aperiam dolore natus perspiciatis rem
              similique!</p>
          </article>
        </el-tab-pane>
        <el-tab-pane label="Буфет" name="second">
          <picture>
            <img src="~/assets/images/dinning-buffet.png" alt="buffet">
          </picture>
          <article>
            <h3>Буфет</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab accusamus commodi, earum enim facere,
              inventore iure, labore laborum nisi obcaecati optio possimus praesentium ratione repudiandae veniam!
              Architecto aut blanditiis dicta, laboriosam maiores, minus necessitatibus praesentium, quam qui rem
              repudiandae temporibus ullam vel veritatis voluptatem. Aperiam dolore natus perspiciatis rem
              similique!</p>
          </article>
        </el-tab-pane>
        <el-tab-pane label="Кофейня" name="third">
          <picture>
            <img src="~/assets/images/kofeynya.png" alt="kofeynya">
          </picture>
          <article>
            <h3>Кофейня</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab accusamus commodi, earum enim facere,
              inventore iure, labore laborum nisi obcaecati optio possimus praesentium ratione repudiandae veniam!
              Architecto aut blanditiis dicta, laboriosam maiores, minus necessitatibus praesentium, quam qui rem
              repudiandae temporibus ullam vel veritatis voluptatem. Aperiam dolore natus perspiciatis rem
              similique!</p>
          </article>
        </el-tab-pane>
      </el-tabs>
    </div>
    <div class="dinning-slider" ref="furshet">
      <article>
        <h3 class="mb-1">Организуем фуршет</h3>
        <p>
          Подберем меню под любой бюджет и для любого мероприятия: от небольшого семейного праздника до масштабного
          корпоратива. Фуршет от Ланч Маркета — это широкий выбор блюд и напитков, внимательное отношение к любым
          пожеланиям клиентов при неизменном качестве обслуживания.
        </p>
      </article>
      <el-carousel :height="($store.getters.screenWidth < 768 ? 250 : 300) + 'px'" :autoplay="false">
        <el-carousel-item v-for="(item, index) in pictures" :key="index">
          <img :src="getImgUrl(item)" alt="furshet" class="picture-100">
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="dinning-form">
      <h3 class="tac">Кейтеринг от Ланч Маркет</h3>
      <Form></Form>
    </div>
  </div>
</template>

<script>
import Form from "~/components/Form";
export default {
  components: {Form},
  head: {
    titleTemplate: '%s - Организация'
  },
  mounted() {
      window.addEventListener('scroll', this.getScrollY)
  },
  destroyed() {
    window.removeEventListener('scroll', this.getScrollY)
  },
  data() {
    return {
      activeName: 'first',
      pictures: ['furshet-1.png', 'furshet-2.png', 'furshet-3.png'],
    };
  },
  methods: {
    getImgUrl(pic) {
      return require('~/assets/images/' + pic)
    },
    scrollIntoElement(element) {
      element.scrollIntoView({behavior: 'smooth', block: 'center'})
    },
    getScrollY() {
      if (window.scrollY > 40) {
        this.$refs.mainNavigation.classList.add('active')
      } else {
        this.$refs.mainNavigation.classList.remove('active')
      }
    }
  }
}
</script>
<style lang="scss">
@import "../../assets/css/variables";
.dinning-content {
  background: url("~/assets/images/dinner-banner.jpg") no-repeat center top / cover;
  border-radius: 5px;
  padding: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
.content-body {
  background-color: white;
  flex: 0 0 500px;
  padding: 2rem;
  box-shadow: 1px 1px 1px 1px $borderGray;
  @media (max-width: 768px) {
    & {
      flex: 0 0 350px;
      padding: 1rem;
    }
  }
}
.dinning-aside {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 5rem;
  @media (max-width: 768px) {
    padding: 2rem;
  }
  .aside-text {
    margin-right: 5rem;
    @media (max-width: 768px) {
      & {
        margin-right: 0;
        margin-bottom: 2rem;
      }
    }
  }
  @media (max-width: 768px) {
    & {
      flex-direction: column;
    }
  }
  .aside-certificate {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    button {
      width: 100%;
      &:first-child {
        margin-bottom: 1rem;
      }
    }
  }
}
.el-tab-pane {
  background-color: $infoGray;
  picture {
    display: flex;
  }
  article {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 2rem;
    h3 {
      margin-bottom: 1rem;
    }
  }
  @media (max-width: 1024px) {
    & {
      display: flex;
      flex-direction: column-reverse;
      article {
        padding: 1rem;
      }
      picture {
        width: 100%;
        img {
          width: 100%;
          height: auto;
        }
      }
    }
  }
}

.dinning-slider {
  margin: 4rem auto;
  max-width: 1000px;
  width: 100%;
  article {
    background-color: $mainGreen;
    padding: 2rem;
    border-radius: 1rem 1rem 0 0;
  }
}
.dinning-form {
  padding: 1rem;
  border-radius: 1rem;
  max-width: 400px;
  width: 90%;
  margin: 0 auto;
}
</style>
