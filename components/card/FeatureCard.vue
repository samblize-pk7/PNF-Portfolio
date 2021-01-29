<template>
  <div class="feature_card">
    <img  :src="data.img" :alt="data.title" />

    <h2>{{ data.title }}</h2>
    <div class="card_des">

    <p>{{ data.paragraph }}</p>
    </div>
  </div>
</template>

<script>

export default {
   data:() =>({
   }),
  props: {
    data: {
      img: String,
      title: String,
      paragraph: String,
    },
  },
};
</script>
<style lang="scss" scoped>
.card_des{
  padding: 20px ;
  background: #0d5c57;
  color: rgb(225, 234, 236);
  border-radius: 8px 8px 40px 8px;
  -webkit-box-shadow: 3px 6px 10px -6px rgba(0,0,0,0.75);
-moz-box-shadow: 3px 6px 10px -6px rgba(0,0,0,0.75);
box-shadow: 3px 6px 10px -6px rgba(0,0,0,0.75);
  p{
    line-height: 2em;
  }

}
.feature_card{
   padding: 32px ;
   display: flex ;
   align-items: center ;
   flex-direction : column ;
   h2{
      padding  : 30px 0 ;
   }
   img{
      width:210px
   }
 
   }

</style>