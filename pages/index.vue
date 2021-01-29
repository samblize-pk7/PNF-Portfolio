<template>
  <div>
    <section id="header_section" class="w-max-1400">
      <div class="flex_row header">
        <img src="~/assets/images/team_hero.png" alt="" />
        <div class="header_content">
          <h1>ما ایده ها رو به تصویر میکشیم</h1>
          <h3>دنبال یه تیم خوب میگردی که :</h3>
          <p class="skills">
            سایت | اپلیکیشن موبایل | برنامه دسکتاپ | وب API و توسعه بک اند
          </p>
        </div>
      </div>
    </section>
    <section id="why_pnf">
      <h1 class="pk-center why_us_title">حالا چرا تیم ما ؟</h1>
      <div class="Feature">
        <FeatureCard
          class="w_1_of_3"
          :data="{
            title: const_data.Features.performance.title,
            img: const_data.Features.performance.img,
            paragraph: const_data.Features.performance.description,
          }"
        />
        <FeatureCard
          class="w_1_of_3"
          :data="{
            title: const_data.Features.affordable.title,
            img: const_data.Features.affordable.img,
            paragraph: const_data.Features.affordable.description,
          }"
        />
        <FeatureCard
          class="w_1_of_3"
          :data="{
            title: const_data.Features.design.title,
            img: const_data.Features.design.img,
            paragraph: const_data.Features.design.description,
          }"
        />
      </div>
    </section>
    <section class="project_section">
      <div class="navigator">
        <div
          class="navigator_item"
          :class="{ active: pNavActive == 'website' }"
          @click="projectNavToggle($event)"
          id="website"
        >
          <div class="bg_animation"></div>
          <a> وبسایت </a>
        </div>
        <div class="divider">|</div>
        <div
          class="navigator_item"
          :class="{ active: pNavActive == 'application' }"
          @click="projectNavToggle($event)"
          id="application"
        >
          <div class="bg_animation"></div>
          <a>اپ موبایل</a>
        </div>
        <div class="divider">|</div>
        <div
          class="navigator_item"
          :class="{ active : pNavActive == 'design' }"
          @click="projectNavToggle($event)"
          id="design"
        >
          <div class="bg_animation"></div>
          <a>طراحی</a>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { Features } from "~/mock/constent_db";
export default {
  data: () => ({
    const_data: {
      Features,
      // this is for project section
    },
      pNavActive: 'design',
  }),
  methods: {
    // this is for project section
    projectNavToggle(event) {
       this.pNavActive = event.currentTarget.id;
    },
  },
};
</script>

<style lang="scss" scoped>
.w_1_of_3 {
  width: 33.33%;
}
.why_us_title {
  font-size: 35px;
  color: rgb(44, 48, 53);
  margin: 30px 0 60px 0;
}
.Feature {
  max-width: 1400px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  @media only screen and (max-width: 1250px) {
    flex-direction: column;
    align-items: center;
    .w_1_of_3 {
      width: auto;
      max-width: 500px;
    }
  }
}
#header_section {
  margin-top: 100px;
  .flex_row {
    img {
      width: 50%;
    }
  }
  @media only screen and (max-width: 950px) {
    .flex_row {
      flex-direction: column;
      align-items: center;
      img {
        width: 80%;
      }
    }
    .header_content {
      margin: auto;
      max-width: 90%;
    }
  }
}
#why_pnf {
  background: #21cec2;
  padding-top: 80px;
  clip-path: polygon(50% 50px, 100% 0%, 100% 100%, 0 100%, 0 0);
  padding-bottom: 150px;
}
.flex_row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
.header {
  margin-top: 50px;
  img {
    width: 55vw;
    @media (max-width: 900px) {
      width: 90vw;
      margin: auto;
    }
  }
}
.header_content {
  width: 50%;
  text-align: right;
  direction: rtl;
  // margin-right: auto;
  display: flex;
  justify-content: center;
  flex-direction: column;

  align-self: stretch;
  // background-color: aquamarine;

  h1 {
    color: #2b00d4;
    padding: 50px 0;
    font-weight: 100;
  }
}
.skills {
  margin-top: 10px;
  font-weight: 600;
  color: rgb(21, 131, 80);
}

.project_section {
  background: rgb(238, 248, 248);
}
.navigator {
  background: #21cec2;
  position: relative;
  top: -30px;
  max-width: 1000px;
  margin: auto;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 10px 20px;
  border: 4px solid #0d5c5754;
  transition: 300ms;
  &:hover {
    border-color: #0d5c57c4;
  }
  border-top: none;
  border-radius: 2px 2px 4px 4px;

  .divider {
    color: #fff;
    font-size: 20px;
  }
  .navigator_item {
    cursor: pointer;
    overflow: hidden;
    height: 40px;
    position: relative;
    a {
      position: relative;
      top: 8px;
      text-decoration: none;
      padding: 0 40px;
      transition: 300ms;
      color: rgb(26, 22, 22);
    }
    .bg_animation {
      top: -40px;
      border-radius: 2px;
      height: 0;
      right: 0px;
      left: 0px;
      // bottom : 0 ;
      position: absolute;
      // width: 100px;
      height: 40px;
      background-color: rgba(9, 48, 51, 0.411);

      border-radius: 0 0 50% 50%;
      transition: 300ms;
    }
    &:hover {
      .bg_animation {
        top: 0px;
        border-radius: 0 0 30% 30%;
      }
      a {
        color: #fff;
      }
    }
    &.active {
      .bg_animation {
        top: 0px;
        border-radius: 0 0 30% 30%;
      }
      a {
        color: #fff;
      }
    }
  }
}
</style>