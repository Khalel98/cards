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
          <li class="nav-items-link">Главная</li>
          <li class="nav-items-link">Возможности</li>
          <li class="nav-items-link">Как получить карту</li>
          <li class="nav-items-link">FAQ</li>
          <li class="nav-items-link">Контакты</li>
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
  },
};
</script>
