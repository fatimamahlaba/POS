<template>
   <div class="section-head">
      <h2></h2>
    </div>
     <div class="row" v-if="projects">
      <div v-for="(project, index) of projects" :key="index.id" class="col-sm-auto col-md-auto col-lg- col-xl- col-xxl" style="height: 300px;">
        <div class="card">
          <img class="card-img-top" :src="project.image" alt="Portfolio practice" style="height: 300px;">

      <div class="card-body">
        <h5 class="card-title">{{project.title}}</h5>
        <a :href="project.github" target="_blank" class="btn" style="display: inline-block; background-color: green"><img src="https://i.postimg.cc/bv8wZrwb/icons8-github-30.png" style="height: 40px; width: 30px ;" alt=""></a>
        <a :href="project.netlify" taget="_blank" class="btn" style="display: inline-block; background-color: green"><img src="https://i.postimg.cc/13kDHd0S/netty.png" style="height: 40px; width: 30px ;" alt=""></a>
      </div>
      
    </div>
  </div>
    </div>
</template>

<script>
// export default {
//   data() {
//       return {
//           products: []
//       };
//   },
// mounted(){
//   fetch("https://pos-fj.herokuapp.com/products")
//   .then(res => res.json())
//   .then(data => {
//     this.projects = data;
//   })
// }
// };

</script>

<style scoped>
.container{
        padding-bottom: 50px;
    }

.btn{
    margin: 10px;
}    
.card{
  margin-top: 200px;
}
</style>