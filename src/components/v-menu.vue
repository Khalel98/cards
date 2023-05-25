<template>
  <div>
    <div class="nav-menu">
      <!--// Menu container -->
      <div class="hamburger-menu-body">
        <div class="nav-menu__logoMobile">
          <img src="../assets/logo.png" alt="" />
        </div>
        <div
          class="hamburger-menu"
          @click="showMenu()"
          :class="this.showMobileMenu ? 'humClicked' : ''"
        >
          <div class="bar-top"></div>
          <div class="bar-middle"></div>
          <div class="bar-bottom"></div>
        </div>
      </div>
      <!--Hamburger icon with click method-->
      <div
        class="nav-content"
        :class="this.showMobileMenu ? 'open-menu' : 'closed-menu'"
      >
        <!--// Menu content-->
        <div class="nav-menu__logoDesktop">
          <img src="../assets/logo.png" alt="" />
        </div>
        <!--// Here can be a logo-->
        <ul class="nav-items">
          <li class="nav-items-link" @click="navigateTo('#main')">Главная</li>
          <li class="nav-items-link" @click="navigateTo('#features')">
            Возможности
          </li>
          <li class="nav-items-link" @click="navigateTo('#step')">
            Как получить карту
          </li>
          <li class="nav-items-link" @click="navigateTo('#faq')">FAQ</li>
          <li class="nav-items-link" @click="navigateTo('#footer')">
            Контакты
          </li>
        </ul>
        <div class="login-button">Войти</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showMobileMenu: false,
    };
  },
  methods: {
    showMenu() {
      this.showMobileMenu = !this.showMobileMenu;
    },
    navigateTo(target) {
      const element = document.querySelector(target);
      window.scrollTo({
        behavior: "smooth",
        top: element.offsetTop,
      });
    },
  },
};
</script>
