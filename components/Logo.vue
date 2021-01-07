<template>
  <div class="grid body_logo">
    <vs-row justify="center" align="center">
      <div class="logo_svg">
        <SvgLogoBlack class="noir_logo" />
        <SvgLogo class="color_logo" />
      </div>
      <div class=" ">
        <vs-col class="logo_text" justify="center" align="start">
          <h2 id="pnf">PNF</h2>
          <h2 id="team">team</h2>
        </vs-col>
      </div>
    </vs-row>
  </div>
</template>

<script>
export default {};
</script>





<style lang="scss" scoped>
.body_logo{
  padding: 15px 0 5px 0;
}

.logo_text {
  h2 {
       color: #2b00d4;

    font-family: Cairo ;
    padding: 0;
    margin: 0;
    font-size: 22px;
    line-height: 23px;
    transition: 250ms ease-in-out;
    cursor: default;
  }
  &:hover {
    #pnf {
    
      transform: rotate(-10deg) skew(20deg) translateY(-5px);
      font-size: 20px;
    }
    #team {
      

      transform: skew(10deg, 10deg) translateY(2px);
      font-size: 24px;
    }
  }
}

.logo_svg {
  position: relative;

  .color_logo {
    top: 0;
    left: 0;
    position: absolute;
    transition: 300ms ease-out;
    transform: scale(0) rotate(180deg);
  }
  .noir_logo {
    transition: 300ms;
  }

  &:hover {
    .noir_logo {
      transform: scale(0) rotate(180deg);
    }
    .color_logo {
      transform: scale(1);
    }
  }
}
</style>

<script>

export default {
  
}
</script>