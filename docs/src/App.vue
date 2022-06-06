<template>
  <div id="app">
    <!-- Header -->
    <header id="header">
      <!-- Mobile Navigation -->
      <nav class="navbar" :class="{ 'navbar--scroll': scrollPosition > 0}">
        <div class="navbar__container">
          <img src="@/assets/images/logo.svg" alt="Company Logo" class="navbar__logo">
          <!-- Mobile Nav Menu -->
          <div class="hamburger" :class="{ 'hamburger--active': mobileNav }" @click="mobileNav = !mobileNav">
            <div class="hamburger__line"></div>
            <div class="hamburger__line"></div>
            <div class="hamburger__line"></div>
          </div>
          <ul class="navigation">
            <li class="navigtion__item">
              <a href="#" class="navigation__link">About</a>
            </li>
            <li class="navigtion__item">
              <a href="#" class="navigation__link">Careers</a>
            </li>
            <li class="navigtion__item">
              <a href="#" class="navigation__link">Events</a>
            </li>
            <li class="navigtion__item">
              <a href="#" class="navigation__link">Products</a>
            </li>
            <li class="navigtion__item">
              <a href="#" class="navigation__link">Support</a>
            </li>
          </ul>
        </div>
      </nav>
      <!-- Mobile Nav Slide -->
      <div class="mobile-nav-tray" :class="{ 'mobile-nav-tray--active': mobileNav }">
        <ul class="mobile-menu">
          <li class="mobile-menu__item" :class="{'mobile-menu__item--active': mobileNav}" :style="{ animationDelay: '.1s' }">
            <a href="" class="mobile-menu__link">About</a>
          </li>
          <li class="mobile-menu__item" :class="{'mobile-menu__item--active': mobileNav}" :style="{ animationDelay: '.2s' }">
            <a href="" class="mobile-menu__link">Careers</a>
          </li>
          <li class="mobile-menu__item" :class="{'mobile-menu__item--active': mobileNav}" :style="{ animationDelay: '.3s' }">
            <a href="" class="mobile-menu__link">Events</a>
          </li>
          <li class="mobile-menu__item" :class="{'mobile-menu__item--active': mobileNav}" :style="{ animationDelay: '.4s' }">
            <a href="" class="mobile-menu__link">Products</a>
          </li>
          <li class="mobile-menu__item" :class="{'mobile-menu__item--active': mobileNav}" :style="{ animationDelay: '.5s' }">
            <a href="" class="mobile-menu__link">Support</a>
          </li>
        </ul>
      </div>
      <div class="headline-wrapper">
        <div class="headline">
          <h1 class="headline__title">Immersive experiences that deliver</h1>
        </div>
      </div>
    </header>
    <!-- Main -->
    <main id="content">
      <section class="leader">
        <img src="@/assets/images/mobile/image-interactive.jpg" alt="Image of man using VR headset" class="leader__image">
        <div class="leader__article">
          <h2 class="leader__title">The leader in interactive VR</h2>
          <p class="leader__body">Founded in 2011, Loopstudios has been producing world-class virtual reality projects for some of the best companies around the globe. Our award-winning creations have transformed businesses through digital experiences that bind to their brand.</p>
        </div>
      </section>
      <section class="creations">
        <h3 class="creations__title">Our Creations</h3>
        <div class="creations__grid">
          <GridCard :title="card.title" :image="card.image" :device="device" v-for="card in cards" :key="card.id"></GridCard>
        </div>
        <button class="creations__btn">See All</button>
      </section>
    </main>
    <!-- Footer -->
    <footer class="footer">
      <div class="footer__wrapper">
        <div class="footer__container">
          <img src="@/assets/images/logo.svg" alt="Company Logo" class="footer__logo">
          <ul class="footer-nav">
            <li class="footer-nav__item">
              <a href="#" class="footer-nav__link">About</a>
            </li>
            <li class="footer-nav__item">
              <a href="#" class="footer-nav__link">Careers</a>
            </li>
            <li class="footer-nav__item">
              <a href="#" class="footer-nav__link">Events</a>
            </li>
            <li class="footer-nav__item">
              <a href="#" class="footer-nav__link">Products</a>
            </li>
            <li class="footer-nav__item">
              <a href="#" class="footer-nav__link">Support</a>
            </li>
          </ul>
        </div>
        <div class="footer__container">
          <div class="social-media">
            <img src="@/assets/images/icons/icon-facebook.svg" alt="Facebook Social Media Logo" class="social-media__logo">
            <img src="@/assets/images/icons/icon-twitter.svg" alt="Twitter Social Media Logo" class="social-media__logo">
            <img src="@/assets/images/icons/icon-pinterest.svg" alt="Pinterest Social Media Logo" class="social-media__logo">
            <img src="@/assets/images/icons/icon-instagram.svg" alt="Instagram Social Media Logo" class="social-media__logo">
          </div>
          <p class="copyright">&#169; 2021 Loopstudios. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import GridCard from '@/components/GridCard';

export default {
  name: 'App',
  components: {
    GridCard
  },
  data() {
    return {
      mobileNav: false,
      scrollPosition: null,
      device: 'mobile',
      cards: [
        { id: 0, title: 'Deep Earth', image: 'deep-earth'},
        { id: 1, title: 'Night Arcade', image: 'night-arcade'},
        { id: 2, title: 'Soccer Team VR', image: 'soccer-team'},
        { id: 3, title: 'The Grid', image: 'grid'},
        { id: 4, title: 'From Up Above VR', image: 'from-above'},
        { id: 5, title: 'Pocket Borealis', image: 'pocket-borealis'},
        { id: 6, title: 'The Curiosity', image: 'curiosity'},
        { id: 7, title: 'Make it Fisheye', image: 'fisheye'}
      ]
    }
  },
  watch: {
    mobileNav() {
      this.mobileNav ? document.documentElement.style.overflow = 'hidden' : document.documentElement.style.overflow = 'auto'
    }
  },
  mounted() {
    window.addEventListener('scroll', this.updateScroll);
    window.addEventListener('resize', this.getWindowSize);
    this.getWindowSize();
  },
  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY
    },
    getWindowSize() {
      window.innerWidth >= 1200 ? this.device = 'desktop' : this.device = 'mobile'
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/style.scss';

body {
  font-family: 'Josefin Sans', sans-serif;
}

#header {
  width: 100%;
  height: 100vh;
  max-height: 700px;
  background-image: linear-gradient(hsl(0,0%,0%, .5), hsl(0,0%,0%, 0)), url('~@/assets/images/mobile/image-hero.jpg');
  background-size: cover;
  display: flex;
  flex-direction: column; 
  justify-content: center;
  align-items: center;
  overflow: hidden;
  @include md {
    height: 50vh;
    min-height: 35rem;
    background-image: linear-gradient(hsl(0,0%,0%, .6), hsl(0,0%,0%, .25)), url('~@/assets/images/desktop/image-hero.jpg');
    background-position: center;
  }
}

.navbar {
  width: 100%;
  position: fixed;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  z-index: 9999;
  padding: 1.5rem;
  transition: all .25s ease;
  margin-top: 1rem;
  &__logo {
    height: 1.5rem;
  }
  &__container {
    width: 100%;
    margin: 0 auto;
    padding: 0 1.5rem;
    display: flex;
    justify-content: space-between;
    max-width: 1260px;
  }
  &--scroll {
    margin-top: 0;
    background: $black;
  }
}

.hamburger {
  width: 25px;
  cursor: pointer;
  &__line {
    position: relative;
    width: 100%;
    height: 2px;
    left: 0;
    margin-bottom: 5px;
    background: hsl(0, 0%, 100%);
    transition: all .3s;
  }
  &--active {
    :nth-child(1) {
      transform: translateY(7px) rotate(45deg);
    }
    :nth-child(2) {
      left: 10rem;
    }
    :nth-child(3) {
      transform: translateY(-7px) rotate(-45deg);
    }
  }
  @include md {
    display: none;
  }
}

.navigation {
  display: none;
  list-style: none;
  gap: 1.5rem;
  margin-top: 6px;
  &__link {
    text-decoration: none;
    color: $white;
    &:after {
      content: "";
      display: block;
      margin: 0 auto;
      width: 0%;
      padding-top: .5rem;
      border-bottom: 2px solid transparent;
      transition: all .35s ease;
    }
    &:hover:after {
      border-bottom: 2px solid $white;
      width: 50%;
    }
  }
  @include md {
    display: flex;
  }
}

.headline-wrapper {
  width: 100%;
  max-width: 1260px;
  padding: 0 1.5rem;
}

.headline {
  width: 26rem;
  max-width: 100%;
  @include lg {
    width: 38rem;
  }
  @include xl {
    width: 40rem;
  }
  &__title {
    border: 2px solid hsl(0, 0%, 100%);
    padding: 1.25rem;
    word-spacing: 10000px;
    font-size: 2.5em;
    text-transform: uppercase;
    color: hsl(0, 0%, 100%);
    @include md {
      word-spacing: 0;
    }
    @include lg {
      font-size: 3.75rem;
    }
    @include xl {
      font-size: 4rem;
    }
  }
}

#content {
  padding: 0 1.5rem;
  max-width: 1260px;
  margin: 0 auto;
}

.leader {
  padding: 5rem 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  @include lg {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: 1fr;
    text-align: left;
    margin-bottom: 3rem;
  }
  &__image {
    width: 100%;
    @include lg {
      grid-row: 1 / 2;
      grid-column: 1 / 5;
    }
  }
  &__article {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: $white;
    @include lg {
      display: block;
      position: relative;
      top: 7rem;
      grid-row: 1 / 3;
      grid-column: 4 / -1;
      padding: 3rem 0 2.5rem 6rem;
      margin-left: 2rem;
    }
  }
  &__title {
    font-size: 2rem;
    text-transform: uppercase;
    margin: 2.5rem 0 1rem;
    max-width: 20ch;
    @include lg {
      font-size: 2.75rem;
      margin-bottom: 1.5rem;
    }
  }
  &__body {
    max-width: 30ch;
    font-size: .925rem;
    font-family: 'Alata', sans-serif;
    color: hsl(0, 0%, 55%);
    line-height: 1.6rem;
    @include md {
      max-width: 45ch;
      // font-size: 1rem;
    }
  }
}

.creations {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 5rem;
  @include lg {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
  &__title {
    font-size: 2rem;
    text-transform: uppercase;
    margin-bottom: 2.5rem;
    @include lg {
      font-size: 2.75rem;
      margin-bottom: 3.5rem;
      margin-right: auto;
      grid-column: 1 / 5;
      grid-row: 1 / 3;
    }
  }
  &__grid {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
    margin-bottom: 2rem;
    overflow: hidden;
    @include md {
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      align-items: flex-start;
    }
    @include lg {
      grid-column: 1 / -1;
      margin-top: 1rem;
    }
  }
  &__btn {
    border: 1px solid hsl(0, 0%, 0%);
    background: transparent;
    font-size: 1rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    font-family: 'Alata', sans-serif;
    padding: .5rem 2.5rem;
    cursor: pointer;
    transition: all .35s ease;
    @include lg {
      grid-column: 4 / -1;
      grid-row: 1 / 2;
      justify-self: end;
    }
    &:hover {
      background-color: $black;
      color: $white;
    }
  }
}

.footer {
  background: hsl(0, 0%, 0%);
  text-align: center;
  padding: 3rem 0;
  &__logo {
    height: 1.4rem;
    margin-bottom: 2rem;
  }
  &__wrapper {
    width: 100%;
    max-width: 1260px;
    margin: 0 auto;
    @include md {
      display: flex;
      justify-content: space-between;
    }
  }
  @include md {
    text-align: left;
    display: flex;
    justify-content: space-between;
    padding: 2.5rem 0 1.5rem;
    &__logo {
      margin-bottom: 1.5rem;
    }
    &__container {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      padding: 0 1.5rem;
      &:last-of-type {
        align-items: flex-end;
        text-align: right;
      }
    }
  }
}

.footer-nav {
  list-style: none;
  margin-bottom: 2.5rem;
  &__item {
    margin-bottom: 1.5rem;
  }
  &__link {
    display: inline-block;
    font-size: .925rem;
    text-decoration: none;
    color: hsl(0, 0%, 100%);
    font-weight: bold;
    &:after {
      content: "";
      display: block;
      margin: 0 auto;
      width: 0%;
      padding-top: .5rem;
      border-bottom: 2px solid transparent;
      transition: all .35s ease;
    }
    &:hover:after {
      border-bottom: 2px solid $white;
      width: 50%;
    }
  }
  @include md {
    display: flex;
    gap: 1.5rem;
    margin-bottom: 0;
  }
}

.social-media {
  margin-bottom: 1.5rem;
  & img {
    margin-left: 1rem;
    cursor: pointer;
    padding-bottom: .35rem;
    border-bottom: 2px solid transparent;
    transition: border .35s ease;
    &:hover {
      border-bottom: 2px solid $white;
    }
  }
}

.copyright {
  font-size: .925rem;
  font-weight: bold;
  color: hsl(0, 0%, 55%);
  @include md {
    margin-top: -.35rem;
  }
}

.mobile-nav-tray {
  position: fixed;
  display: flex;
  align-items: center;
  top: 100%;
  left: 0;
  z-index: 999;
  min-width: 100%;
  min-height: 100vh;
  padding-left: 1.5rem;
  background: hsl(0, 0%, 0%);
  transition: top .5s ease;
  &--active {
    top: 0;
  }
}

.mobile-menu {
  list-style: none;
  &__item {
    position: relative;
    top: 100rem;
    margin-bottom: 1.5rem;
    &--active {
      animation: slide-up 0.5s forwards;
    }
  }
  &__link {
    color: hsl(0, 0%, 100%);
    text-decoration: none;
    font-size: 1.8rem;
    text-transform: uppercase;
  }
}

// Keyframes
@keyframes slide-up {
    100% { top: 0; }
}
</style>
