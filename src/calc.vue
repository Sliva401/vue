<template>
    <div class="calc-section">
        <div class="calculate-panel">
            <div class="display">
                <div class="first-row calc-row">{{this.rows[0]}}</div>
                <div class="second-row calc-row">{{this.rows[1]}}</div>
                <div class="third-row calc-row">{{this.rows[2]}}</div>
            </div>
            <div class="btns">
                <div class="btn" @click="deleteAll">c</div>
                <div class="btn sqrt" @click="sqrtNum">&#8730;</div>
                <div class="btn delete" @click="deleteNum">&lt;</div>
                <div class="btn" @click="enter(1)">1</div>
                <div class="btn" @click="enter(2)">2</div>
                <div class="btn" @click="enter(3)">3</div>
                <div class="btn" @click="oper('/')" > /</div>
                <div class="btn" @click="enter(4)">4</div>
                <div class="btn" @click="enter(5)">5</div>
                <div class="btn" @click="enter(6)">6</div>
                <div class="btn" @click="oper('*')">x</div>
                <div class="btn" @click="enter(7)">7</div>
                <div class="btn" @click="enter(8)">8</div>
                <div class="btn" @click="enter(9)">9</div>
                <div class="btn" @click="enter('.')">,</div>
                <div class="btn" @click="enter(0)">0</div>
                <div class="btn" @click="oper('+')">+</div>
                <div class="btn" @click="oper('-')">-</div>
                <div class="btn" @click="getResult">=</div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    
            
            data() {
        return {
            rows: ['','',''],
            index: 0,
            result: '',
            afterResult: false
            
        }
},
methods: {
    enter (num) {
        if(this.afterResult) {this.rows[1]='';this.afterResult = false}
        if (this.index===1) {this.index=2}
        if(this.rows[this.index].length<18) {this.rows[this.index]+= num}
        
        
        
    },
    oper(num) {
      if(this.afterResult) {this.rows[0]=this.rows[1]; this.rows[1]='';this.afterResult = false}
      if(this.index===0&this.rows[this.index]!=='') {
        this.index = 1
        this.rows[this.index] = num
      } else {
      if(this.index===1) { this.rows[this.index] = num} 
      
    }
    },
   
    deleteAll() {
        this.rows[0] = ''
        this.rows[1] = ''
        this.rows[2] = ''
        this.index = 0

    },
    deleteNum() {
         if(this.rows[this.index]===''&this.index!==0) {this.index--}
         this.rows[this.index]=this.rows[this.index].slice(0,-1)
    },
   
    getResult() {
        this.rows[1]=eval(this.rows[0]+this.rows[1]+this.rows[2]);
        
         
        this.rows[0] = ''
        this.rows[2] = ''
        this.index = 0
        if(this.rows[1]>9999999999999) {this.rows[1]='Слишком большое число!'}
        this.afterResult = true 
    },
    sqrtNum() {
        if (this.index!==1) {this.rows[this.index]= Math.sqrt(this.rows[this.index])}
        
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
.calc-section {
    padding: 100px 0;
    background-color: rgb(179, 173, 173);
    max-width: 1920px;
    margin: 0 auto;
}
     .calculate-panel {
        height: 628px;
        width: 400px;
        margin: 0 auto;
        background-color: rgb(153, 203, 204);
        padding-top: 10px;
        border-radius: 20px;
        margin-top: 40px;
        padding: 25px;
        color: black;
        border: 3px solid black;
        
    }
    .display {
        height: 200px;
        background-color: rgb(224, 255, 207);
        border: 3px solid gray;
        font-size: 40px;
        display: flex;
        justify-content: center;
        align-items: end;
        flex-direction: column;
        padding: 5px;
       color: rgb(48, 48, 48);
       text-align: center;
    }
    .btns {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        justify-items: center;
        margin-top: 39px;
    }
    .btn {
        width: 70px;
        height: 60px;
        border-radius: 30%;
        cursor: pointer;
        background-color: rgb(237, 237, 237);
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        margin-bottom: 10px;
        border: 1px solid rgb(97, 97, 97);
        user-select: none;
    }
    .btn:hover {
        box-shadow: 0 0 15px 1px black;
    }
    .btn:active {
        border: 5px solid rgb(0, 0, 0);
    }
    .delete {
        grid-column: span 2;
        width: 150px;
        border-radius: 10px;

    }
    .sqrt {
        font-size: 20px;
    }
    .calc-row {
        height: 30%;
        font-size: 30px;
        
    }
</style>