<template>
  <div id="calculat">
    <h4>计算器</h4>
    <input type="text" class='input' v-model='inContnet'>
    <ul @click='press' class= 'presCont'>
      <li>7</li>
      <li>8</li>
      <li>9</li>
      <li>&lt=</li>
      <li>C</li>
      <li>4</li>
      <li>5</li>
      <li>6</li>
      <li>+</li>
      <li>-</li>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>*</li>
      <li>/</li>
      <li>%</li>
      <li>0</li>
      <li>.</li>
      <li class='eqBtn'>=</li>  
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      inContnet: '',
      reString: '',
      count: 0
    }
  },
  methods: {
    press: function(event){
     var inString = event.target.innerHTML;
     if(inString !='=' && inString !='C' && inString !='&lt;='){
      this.reString += inString;
      this.inContnet = this.reString;
     }else if(inString == 'C'){
       this.inContnet = '';
       this.reString = '';
     }else if(inString =='&lt;='){
       var n = this.inContnet.length;
       this.inContnet = this.inContnet.substring(0,n-1);
     }else if(inString == '='){
      var s = eval(this.inContnet);
      var finite = isFinite(s);
      if(finite){
        this.inContnet = s;
        this.reString = s;
      }else{
        this.inContnet = '错误';
        this.reString = '';
      }
     }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#calculat{
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  margin:0 auto;
  width: 600px;
  background-color: #f5f5f5;
}
#calculat>h4{
  height: 60px;
  line-height: 60px;
  padding: 0;
  margin: 0;
  background-color: #f5f5f5;
}
.input{
  width: 558px;
  height: 90px;
  border: none;
  padding: 0 20px;
  text-align: right;
  font-size: 30px;
}
.presCont{
  padding: 0;
  margin: 0;
  display: flex;
  list-style: none;
  flex-wrap: wrap;
}
.presCont>li{
  font-size: 24px;
  height: 90px;
  line-height: 90px;
  width: 118px;
  text-align: center;
  border: 1px solid #ddd;
  background-color: #f5f5f5f5;
  cursor: pointer;
}
.presCont>li:hover{
  
}
.presCont>.eqBtn{
  background-color: #3B8BF2;
  font-size: 40px;
  color: #fff;
  width: 236px;
}
</style>
