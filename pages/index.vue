<template>
  <div>
    <section id="header_section">
      <div class="flex_row header">
        <img src="~/assets/image/team_hero.png" alt="" />
        <div class="header_content">
          <h1>ما ایده ها رو به تصویر میکشیم</h1>
          <h3>دنبال یه تیم خوب میگردی که :</h3>
          <p class="skills">سایت | اپلیکیشن موبایل | برنامه دسکتاپ | وب API و توسعه بک اند</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  //     methods: {
  //     handleScroll () {
  //       // Your scroll handling here
  //       // console.log(window.scrollY)
  //     }
  //   },
  //   beforeMount () {
  //     window.addEventListener('scroll', this.handleScroll);
  //   },
  //   beforeDestroy() {
  //     window.removeEventListener('scroll', this.handleScroll);
  //   }
};
</script>

<style lang="scss" scoped>
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
      text-align: right;
      direction: rtl;
      margin-right: auto;
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
</style>