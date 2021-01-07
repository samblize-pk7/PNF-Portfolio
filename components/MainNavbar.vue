   <template>
  <div>
    <vs-navbar
      class="nav_margin"
      :class="{ shadow: goAnimate }"
      v-model="active"
    >
      <template #left>
        <Logo class="" :style="scrollVar" />
      </template>
      <template #right>
        <vs-navbar-item :active="active == 'Blog'" id="Blog">
          {{ const_db.menuItem.BlogPage }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Contact'" id="Contact">
          {{ const_db.menuItem.ContactUs }}
        </vs-navbar-item>  
        <vs-navbar-item :active="active == 'Services'" id="Services">
          {{ const_db.menuItem.Services }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Projects'" id="Projects">
          {{ const_db.menuItem.ProjectsArchive }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'About'" id="About">
          {{ const_db.menuItem.AboutUs }}
        </vs-navbar-item>
        <vs-navbar-item :active="active == 'Home'" id="Home">
          {{ const_db.menuItem.HomePage }} 
        </vs-navbar-item>
      </template>
    </vs-navbar>
  </div>
</template>




<script >
import { menuItem } from "~/mock/constent_db.js";
export default {
  props: {
    height: {
      type: Number,
      default: 50,
    },
    scale: {
      type: Number,
      default: 1,
    },
  },
  computed: {
    scrollVar() {
      return {
        height: `${this.height}px`,

        transform: `scale(${this.scale})`,
      };
    },
  },

  methods: {
    handleScroll() {
      // Your scroll handling here
      var scrollEvent = window.scrollY;
      console.log(scrollEvent);
      if (scrollEvent >= 100) {
        this.goAnimate = true;

        if (this.height >= 36) {
          this.height = 50 - (14 * (scrollEvent - 100)) / 100;
        }
        if (this.scale >= 0.5) {
          this.scale = 1 - (0.5 * (scrollEvent - 100)) / 100;
        }
      } else {
        this.goAnimate = false;
        if (this.height != 50) {
          this.height = 36 - 14 * ((scrollEvent - 100) / 100);
        }
        if (this.scale != 1) {
          this.scale = 0.5 - (0.5 * (scrollEvent - 100)) / 100;
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
  data: () => ({
    active: 'Home',
    goAnimate: false,
    const_db: {
      menuItem,
      
    },
  }),
};
</script>



<style lang="scss" scoped>
.nav_margin {
  position: fixed;
  top: 0;
}
.shadow {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
</style>