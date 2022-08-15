<template>
  <Calc />
  <Todo />
  <div class="slider-section">
     <div class="btn" @click="indexDown()"><img src="https://cdn-icons-png.flaticon.com/512/271/271228.png"></div>
       <div class="slider">
       
           <img src="https://w-dog.ru/wallpapers/9/8/549551266186127/kananaskis-alberta-kanada-nebo-oblaka-gory-les-derevya-el-priroda-zakat-ozero-vecher-kamni-otrazhenie.jpg" alt="" class="img ">
           <img src="https://www.nastol.com.ua/download.php?img=201408/1680x1050/nastol.com.ua-108611.jpg" alt="" class="img" :style="{transform: itemMargin[4],transition:transit}">
           <img src="https://img3.akspic.ru/attachments/crops/8/0/5/5/45508/45508-nauka-nebo-ozero_pejto-pustynya-ekosistema-1280x720.jpg" alt="" class="img" :style="{transform: itemMargin[3],transition:transit}">
           <img src="https://kaifolog.ru/uploads/posts/2015-04/1429884887_004.jpg" alt="" class="img" :style="{transform: itemMargin[2],transition:transit}">
           <img src="https://w-dog.ru/wallpapers/11/14/428271315679795/geran-kislicy-sirenevye-cvety-lepestki-polyana-makro-razmytost.jpg" alt="" class="img" :style="{transform: itemMargin[1],transition:transit}" >
           <img src="https://w-dog.ru/wallpapers/9/8/549551266186127/kananaskis-alberta-kanada-nebo-oblaka-gory-les-derevya-el-priroda-zakat-ozero-vecher-kamni-otrazhenie.jpg" alt="" class="img" :style="{transform: itemMargin[0],transition:transit}" >
           
           
       </div>
      <div class="btn" @click="indexUp()"><img src="https://cdn-icons-png.flaticon.com/512/271/271228.png"></div>
      
  </div>
  <Plus />
  
</template>

<script>
import Calc from './calc'
import Todo from './todo'
import Plus from './weather.vue'
export default {
  components: {Calc,Todo,Plus},
  data() {
    return{
      itemMargin: ['none','none','none','none','none'],
      index: 0,
      transit: '1.2s',
      itemMarginZero: ['translateX(0)','translateX(0)','translateX(0)','translateX(0)','translateX(0)']
     
        
    }
  },
  methods: {
    
      indexUp() {
        this.transit= '1.2s'
        let negative = Math.abs(this.index);
         if (this.index<0) {this.index++;this.itemMargin[negative] = 'translateX(0)';} else {
         if(this.index===4) {
          this.itemMargin[this.index] = 'translateX(1000px)'
          
       setTimeout(()=>{this.transit = '0s';this.itemMargin = ['translateX(0)','translateX(0)','translateX(0)','translateX(0)','translateX(0)'];this.index = 0;}, 600)    
      
        } else {this.itemMargin[this.index] = 'translateX(1000px)'
         this.index++;}
      }},
      indexDown() {
        this.transit= '1.2s'
        let negative = Math.abs(this.index);
         if (this.index>0) {this.index--;this.itemMargin[this.index] = 'translateX(0)';} else {
         if(negative===4) {
          this.itemMargin[negative] = 'translateX(-1000px)'
          
       setTimeout(()=>{this.transit = '0s';this.itemMargin = ['translateX(0)','translateX(0)','translateX(0)','translateX(0)','translateX(0)'];this.index = 0;}, 600)    
      
        } else {this.itemMargin[negative] = 'translateX(-1000px)'
         this.index--;}
       
      
               
         }
      
  //
    }
  

}
}
</script>

<style scoped>
   * {
	vertical-align: baseline;
  font-weight: inherit;
	font-family: inherit;
	font-style: inherit;
	font-size: 100%;
	border: 0 none;
	outline: 0;
	padding: 0;
	margin: 0;
  box-sizing: border-box;
	}
   .slider-section {
    padding: 100px 0;
    background-color: rgb(146, 202, 219);
    max-width: 1920px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    

   }
   .slider-wrapper {
    display: flex;
   }
   
   .img {
    width: 100%;
    height: 100%;
    position: absolute;
    user-select: none;
    
    
    
   }
   .slider {
    position: relative;
     overflow: hidden; 
    width: 1000px;
    height: 590px;
    margin: 0 auto;
    box-shadow: 0 0 10px 1px black;
   }
  
   .btn {
    background-color: white;
    flex-grow: 1;
    opacity: 0.2;
    height: 590px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: 0.5s;
    user-select: none;
   }
   .btn:active {
    opacity: 0.4;
   }
   .btn:hover {
    background-color: rgb(83, 1, 248);
   }
   .btn img {
    width: 100px;
    height: 100px;
   }
   .btn:nth-of-type(1) {
    transform: rotate(-180deg);
   }
   .btn:hover img {
    transform: scale(1.05);
   }
   .btn:active img {
    transform: scale(0.95);
   }
  
   
    
</style>
