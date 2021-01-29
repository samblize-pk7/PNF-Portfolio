<template>
  <div class="grid">
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
@keyframes bounce-down {
  0% {
    transform: rotate(5deg) skew(-20deg, 1deg) translateY(-5px);
    color: #2b00d4;
  }
  50% {
    color: #eb4182;

    transform: rotate(5deg) skew(-20deg, 1deg) translateY(-3px);
  }
  100% {
    color: #2b00d4;
    transform: rotate(5deg) skew(-20deg, 1deg) translateY(-5px);
  }
}
@keyframes bounce-up {
  0% {
    transform: skew(20deg, 9deg) translateY(2px) rotate(-5deg);
    color: #2b00d4;
  }
  50% {
    color: #eb4182;

    transform: skew(20deg, 9deg) translateY(0px) rotate(-5deg);
  }
  100% {
    transform: skew(20deg, 9deg) translateY(2px) rotate(-5deg);
    color: #2b00d4;
  }
}
.logo_text {
  h2 {
    color: #2b00d4;

    font-family: Cairo;
    padding: 0;
    margin: 0;
    font-size: 22px;
    line-height: 23px;
    transition: 300ms ease-in-out;
    cursor: default;
  }
  &:hover {
    #pnf {
      transform: rotate(5deg) skew(-20deg, 1deg) translateY(-5px);
      font-size: 20px;
      animation: bounce-down 1s infinite;
      animation-delay: 400ms;
    }
    #team {
      transform: skew(20deg, 9deg) translateY(2px) rotate(-5deg);
      // font-size: 24px;
      animation: bounce-up 1s infinite;
      animation-delay: 400ms;
    }
  }
}

.logo_svg {
  position: relative;

  .color_logo {
    top: 0;
    left: 0;
    position: absolute;
    transition: 400ms ease-out;
    transform: scale(0) rotate(90deg);
  }
  .noir_logo {
    transition: 400ms ease-out;
  }
  @keyframes blink {
    0% {
      opacity: 1;
      transform: rotate(0deg);
    }
    50% {
      transform: rotate(5deg);
      opacity: 0.7;
    }
    100% {
      transform: rotate(0deg);
      opacity: 1;
    }
  }
  &:hover {
    .noir_logo {
      transform: scale(0) rotate(90deg);
    }
    .color_logo {
      transform: scale(1);
      animation: blink 1s infinite;
      animation-delay: 450ms;
    }
  }
}
</style>

<script>
export default {};
</script>