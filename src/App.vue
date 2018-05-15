<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
    <button @click="start()" type="button" name="button">
      開始
    </button>
    <button @click="restart()" type="button" name="button">
      重新開始
    </button>
    <div class="gameSection">

      <div v-for="o in objects">
        <div class="object">
          <img src="./assets/logo.png" alt="">
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{

      objects:[]
    }
  },
  methods:{
    restart(){
      location.reload();
    },
    start(){
      var o = document.querySelectorAll('.object')
      console.log(o.length);
      var n = 0
      var interv = setInterval(function(){
        if(n<o.length){
          o[n].classList.add('move')
          n++
        }
        else {
          clearInterval(interv)
          var ans = prompt("請問有幾個vue");
          if(ans == o.length){
            alert('答對拉');
          }
          else {
            alert('眼殘尼？是' + o.length + '個');
          }
        }
      }, 200)

    }
  },
  mounted(){
    var num = Math.random() * (15 - 10) + 10
    console.log(num);
    for(let i = 0 ; i < num ; i++){
      console.log('work');
      this.objects.push(i)
    }
    console.log(this.objects);

  }
}
</script>

<style>
/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
#app {
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
.gameSection{
  width: 800px;
  height: 600px;
  background: #EEE;
  position: relative;
  display: flex;
  align-items: center;
}
.object{
  position: absolute;
  top:209px;
  right: 0;
  transition: 0.5s ease-in-out;
  /* position: absolute; */
  /* right: 0 */
}
.move{
  transform: translate(-600px, 0px)
}


</style>
