      <template>
      <div class="kol">
        <div style="height: 23px;"></div>
        <div class="inpk">
    <input  @keyup.enter="send" type="text" class="inp" v-model="city" placeholder="give me city name">
    <button pill variant="info"  @click="send" style="margin-right: -9px; background-color: rgb(230, 229, 229);">
      <svg style="background-color: rgb(230, 229, 229);" class="svg-icon search-icon" aria-labelledby="title desc" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 19.9 19.7"><title id="title">Search Icon</title><desc id="desc">A magnifying glass icon.</desc><g class="search-path" fill="none" stroke="#848F91"><path stroke-linecap="square" d="M18.5 18.3l-5.4-5.4"/><circle cx="8" cy="8" r="7"/></g></svg>

    </button>
     </div>
    
     <div class="inf" v-if=" w!==' ' ">
      <div v-if="loading" style="text-align: center;font-size: larger; font-family: Arial, Helvetica, sans-serif" > <h4 style="color:aliceblue;">Loading... </h4></div>
      <div  v-if="error" style="text-align: center;font-size: larger; font-family: Arial, Helvetica, sans-serif" > <h4 style="color: #990000;">{{ error }}</h4></div>
        <div v-if="dataw" >
      <div class="th"><h2 ></h2><section class="sk">{{dataw.sys.country}}</section></div>
              <h3 style="margin-top: -2px; margin-bottom: -5px;">{{dataw.name}}</h3>
         <h1 style="margin-top: -5px;" >{{ Math.floor(dataw.main.temp)-273 }}C°</h1>
         
         <h1 style="margin-top: -17px;margin-bottom: 9px;">{{ Math.floor(dataw.main.temp)}} F°</h1>
        <h3>  {{dataw.weather[0].description}} </h3>
     </div></div>
      </div>
      </template>
    
 
    
    <script setup>
  import { ref } from 'vue';
  
  const city = ref('');
  const dataw = ref(null);
  const loading = ref(false);
  const error = ref('');
  
  const send = async () => {
    loading.value = true;
    error.value = '';
    dataw.value = null;
  
    try {
      const data = await $fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city.value}&appid=be84c9643dc058716641aa622df6559d`);
      dataw.value = data;
    } catch (err) {
      error.value = 'Not found';
    } finally {
      loading.value = false;
    }
  }
  
</script>
    <style scoped>
    button{ border: none;}
   .svg-icon.search-icon {
  display: inline-block;
  width: 25px;
  height: 20px;

  /* On hover: blue strokes */
  &:focus,
  &:hover {
    .search-path {
      stroke: #299ecc;
    }
  }

  /* On click: thicker black strokes  */
  &:active {
    .search-path {
      stroke: #111516;
      stroke-width: 2px;
    }
  }
}

.button-3 {
  appearance: none;
  background-color: #2ea44f;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}
input:focus {
    border:none; /* یا هر رنگ دیگری که می‌خواهید برای حالت فوکوس */
    outline: none; /* حذف حاشیه پیش‌فرض */
}
.button-3:focus:not(:focus-visible):not(.focus-visible) {
  box-shadow: none;
  outline: none;
}

.button-3:hover {
  background-color: #2c974b;
}

.button-3:focus {
  box-shadow: rgba(46, 164, 79, .4) 0 0 0 3px;
  outline: none;
}

.button-3:disabled {
  background-color: #94d3a2;
  border-color: rgba(27, 31, 35, .1);
  color: rgba(255, 255, 255, .8);
  cursor: default;
}

.button-3:active {
  background-color: #298e46;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}
    .kol{position: absolute; 
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
        background: url(https://dl4.fara-download.ir/imgfa/2020/12/28/q_imgfa_ir__5fe9e3d3b9c32_1.jpg);
        
         background-repeat: no-repeat;
         background-size: cover;
         margin: 0PX;
        }
    .inp{border: none;
        width: 330px;
      height: 27px;
      border-radius: 5px;
      background-color: rgb(230, 229, 229);
      padding-left: 5px;
      }
      .inpk{background-color: rgb(230, 229, 229);
     border-radius: 18px;
      width: 400px;
    
      margin: 0 auto;
    margin-bottom: 20PX;display: flex;}
    .inf{color: aliceblue;
        width: 190px;
        margin: 0 auto; 
        text-align: center;
        background-color: rgba(106, 101, 101, 0.486);
        border-radius: 10px;
        padding: 3px;}
        .sk{margin: 0 4px;
             font-size: large;
            
        
         background-color: rgb(107, 107, 211);
         width: fit-content;
        border-radius: 4px;
        padding: 2px;
        }
         h2{margin: 0px;width: fit-content;}
         .th{display: flex;margin: 0 auto;width: fit-content;}
         button{width: fit-content;
         }
          h3{margin-top: -15px;}
          h1{margin-top: 12px; margin-bottom:6px ;}
          @media (max-width:703px){ 
            .kol{margin: 0px; }
            .inpk{width: 200px; margin: 0 auto; margin-bottom: 26px;}
            h1{margin-top: 6px; margin-bottom: 6px;}
                }
    </style>