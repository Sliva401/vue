<template>
    <div>
        <div class="weather">
           <div class="sun">
               <div class="clouds"></div>
               <div class="rain">/ / / /</div>
           </div>
           
           
           <div class="degrees">{{weather}}</div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return{
            weather: '+10'
        }
    }
    
}
</script>
<style scoped>
.weather {
    background-color: rgb(80, 77, 135);
    height: 700px;
    max-width: 1920px;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
}
.sun {
    border-radius: 50%;
  background: linear-gradient(243.85deg, #F1FF50 16.29%, #FCFF7B 60.89%, rgba(253, 255, 170, 0.81) 99.32%);
    box-shadow: 0 0 50px 1px yellow;

    width: 200px;
    height: 200px;
}
.degrees {
    color: white;
    font-size: 90px;
    font-family:'Courier New', Courier, monospace;
}
.clouds {
    width: 200px;
    height: 100px;
    border-radius: 35%;
    filter: blur(13px);
    position: relative;
    bottom: -80px;
    left: -50px;

    background-color: rgba(214, 214, 242, 0.8);
}
.rain {
    font-size: 50px;
    color: rgb(4, 0, 254);
    position: relative;
    bottom: -60px;
    
}
</style>