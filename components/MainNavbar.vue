<template>
  <div>
    <vs-navbar class="wide_screen_menu" fixed shadowScroll v-model="active">
      <template>
         <vs-tooltip bottom>
        <Logo class="logo_speace" :style="scrollVar" />
        <template #tooltip>
         برای پروژه بعدی حتما روی ما حساب کنید 💚
        </template>
      </vs-tooltip>
        <vs-navbar-item :active="active == 'Home'" id="Home">
          {{ const_db.menuItem.HomePage }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'About'" id="About">
          {{ const_db.menuItem.AboutUs }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Projects'" id="Projects">
          {{ const_db.menuItem.ProjectsArchive }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Blog'" id="Blog">
          {{ const_db.menuItem.BlogPage }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Contact'" id="Contact">
          {{ const_db.menuItem.ContactUs }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Services'" id="Services">
          {{ const_db.menuItem.Services }}
        </vs-navbar-item>
      </template>
    </vs-navbar>

    <div class="mobile_menu">
      <vs-navbar fixed shadowScroll v-model="active">
        <template #left>
          <Logo class="logo_speace" :style="scrollVar" />
        </template>
        <template #right>
          <img
            class="humberger_icon"
            src="/icon-font/menu.svg"
            alt="menu"
            v-on:click="toggleMenu()"
          />
        </template>
      </vs-navbar>
      <transition name="fade">
        <div
          v-if="mobileMenu"
          class="collapsed_menu"
          :class="{ open: mobileMenu}"
        >
          <nav>
            <ul>
              <li>{{ const_db.menuItem.HomePage }}</li>
              <li>{{ const_db.menuItem.AboutUs }}</li>
              <li>{{ const_db.menuItem.ProjectsArchive }}</li>
              <li>{{ const_db.menuItem.BlogPage }}</li>
              <li>{{ const_db.menuItem.ContactUs }}</li>
              <li>{{ const_db.menuItem.Services }}</li>
            </ul>
          </nav>
        </div>
      </transition>
    </div>
  </div>
</template>



<style lang="scss" scoped>
.logo_speace {
  padding: 10px 0 10px 50px;
}
.wide_screen_menu {
  @media only screen and (max-width: 900px) {
    display: none;
  }
}
.mobile_menu {
  display: none;
  @media only screen and (max-width: 900px) {
    display: block;
    .logo_speace {
      padding: 10px;
    }
  }
  .humberger_icon {
    width: 35px;
  }
  .collapsed_menu {
    position: fixed;
    z-index: 2;
    top: 0px;
    bottom: 0;
    -webkit-box-shadow: 3px 6px 10px -6px rgba(0, 0, 0, 0.75);
    -moz-box-shadow: 3px 6px 10px -6px rgba(0, 0, 0, 0.75);
    box-shadow: 3px 6px 10px -6px rgba(0, 0, 0, 0.75);
    left: -200px;
    width: 200px;
    background-color: #00d4d4f5;
    nav {
      margin: 100px 20px 0 30px;

      ul {
        list-style-type: none;
        li {
          color: rgb(24, 26, 29);
          font-weight: 600;
          font-size: 13px;
          margin: 5px 0;
          padding: 10px 0;
          border-bottom: 2px solid rgba(0, 0, 0, 0.123);
        }
      }
    }
  }
}
.open {
  animation: menu_animation 250ms ease-in forwards;
}

@keyframes menu_animation {
  from {
    // transform: translate(-200px, 10px);
    left: -200px;
  }
  to {
    // transform: translate(0px, 0px);
    left: 0px;
  }
}

.fade-enter-active {
  transition: all 0.4s ease-out;
}
.fade-leave-active {
  transition: all 0.3s ease-out;
}
.fade-enter,
.fade-leave-to {
  transform: translate(-200px,-150px);
  border-radius:  0  0 50% 0;
  // opacity: 0;

  
}
</style>

<script >
import { menuItem } from "~/mock/constent_db.js";
export default {
  data: () => ({
    /**
     * the height property of logo
     */
    height: {
      type: Number,
      default: 50,
    },
    /**
     * the Scale property of logo
     */
    scale: {
      type: Number,
      default: 1,
    },
    active: "Home",
    goAnimate: false,
    const_db: {
      menuItem,
    },
    // toggle the humberger menu
    mobileMenu: false,
  }),

  computed: {
    scrollVar() {
      return {
        height: `${this.height}px`,

        transform: `scale(${this.scale})`,
      };
    },
  },

  methods: {
    toggleMenu() {
      this.mobileMenu = !this.mobileMenu;
      console.log(this.mobileMenu);
    },
    handleScroll() {
      // Your scroll handling here
      var scrollEvent = window.scrollY;
      console.log(scrollEvent);
      if (scrollEvent >= 100) {
        this.goAnimate = true;

        if (this.height >= 40) {
          this.height = 50 - (10 * (scrollEvent - 100)) / 100;
        }
        if (this.scale >= 0.7) {
          this.scale = 1 - (0.3 * (scrollEvent - 100)) / 100;
        }
      } else {
        this.goAnimate = false;
        if (this.height != 50) {
          this.height = 40 - 10 * ((scrollEvent - 100) / 100);
        }
        if (this.scale != 1) {
          this.scale = 0.7 - (0.3 * (scrollEvent - 100)) / 100;
        }
      }
    },
  },
  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>


