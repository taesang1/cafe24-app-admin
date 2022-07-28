<template>
  <div>
    <Tutorial/>
    <b-container class="bv-example-row" style="width: 70%">
      <b-row style="margin-top: 150px">
        <b-col style="max-width: 30%">
          <h1>유사상품 추천하기</h1>
          <span>쇼핑몰을 둘러보는 고객에게 관련상품을 추천해보세요.</span>
        </b-col>
        <b-col>
          <div style="display: flex; padding: 30px 40px;">
            <div style="width: 80%">
              <h2>전체 구좌 삽입하기</h2>
            </div>
            <div>
              <label @click="click_toggle" for="toggle" class="toggleSwitch">
                <span class="toggleButton"></span>
              </label>
            </div>
          </div>
          <div style="display: flex; padding: 30px 40px;">
            <div style="width: 80%">
              <p style="font-weight: 900;">SET 1</p>
              <h2>유사상품 추천하기</h2>
              <span>이 기능을 활성화하면 고객이 아이템 상세 페이지 에서 유사상품을 확인할 수 있습니다.</span>
            </div>
            <div style="zoom: 2; margin: auto;">
              <b-form-checkbox
                id="similar_checkbox"
                v-model="similar_status"
                name="similar_checkbox"
                value="on"
                unchecked-value="off"
                @change="similar"
              ></b-form-checkbox>
              <div style="font-size: 10px">State: <strong>{{ similar_status }}</strong></div>
            </div>
          </div>
          
          <div style="display: flex; padding: 30px 40px;">
            <div style="width: 80%">
              <p style="font-weight: 900;">SET 2</p>
              <h2>코디상품 추천하기</h2>
              <span>이 기능을 활성화하면 고객이 아이템 상세 페이지에서 코디상품을 확인할 수 있습니다.</span>
            </div>
            <div style="zoom: 2; margin: auto;">
              <b-form-checkbox
                id="code_checkbox"
                v-model="code_status"
                name="code_checkbox"
                value="on"
                unchecked-value="off"
                @change="code"
              ></b-form-checkbox>
              <div style="font-size: 10px">State: <strong>{{ code_status }}</strong></div>
            </div>
          </div>
          
          <div style="display: flex; padding: 30px 40px;">
            <div style="width: 80%">
              <h2>스크립트 삽입하기</h2>
            </div>
               <label @click="click_script" for="toggle" class="toggleSwitch_2">
                <span class="toggleButton_2"></span>
              </label>
          </div>

        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<style scoped>
.toggleSwitch {
  width: 100px;
  height: 50px;
  display: block;
  position: relative;
  border-radius: 2rem;
  background-color: #fff;
  box-shadow: 0 0 1rem 3px rgba(0 0 0 / 15%);
  cursor: pointer;
}

.toggleSwitch .toggleButton {
  width: 40px;
  height: 40px;
  position: absolute;
  top: 50%;
  left: .2rem;
  transform: translateY(-50%);
  border-radius: 50%;
  background: #007BFF;
}

/* 체크박스가 체크되면 변경 이벤트 */
.toggleSwitch.active {
  background: #007BFF;
}

.toggleSwitch.active .toggleButton {
  left: calc(100% - 2.8rem);
  background: #fff;
}

.toggleSwitch, .toggleButton {
  transition: all 0.2s ease-in;
}

/* 2번째 토글 버튼 */
.toggleSwitch_2 {
  width: 100px;
  height: 50px;
  display: block;
  position: relative;
  border-radius: 2rem;
  background-color: #fff;
  box-shadow: 0 0 1rem 3px rgba(0 0 0 / 15%);
  cursor: pointer;
}

.toggleSwitch_2 .toggleButton_2 {
  width: 40px;
  height: 40px;
  position: absolute;
  top: 50%;
  left: .2rem;
  transform: translateY(-50%);
  border-radius: 50%;
  background: #007BFF;
}

/* 체크박스가 체크되면 변경 이벤트 */
.toggleSwitch_2.active {
  background: #007BFF;
}

.toggleSwitch_2.active .toggleButton_2 {
  left: calc(100% - 2.8rem);
  background: #fff;
}

.toggleSwitch_2, .toggleButton_2 {
  transition: all 0.2s ease-in;
}
</style>
<script>
var toggle_2 =''
var toggle = ''
var code_status = 'off'
var similar_status = 'off'
var difftimeH = ''
var difftimeM = ''
export default {
  name: 'IndexPage',
    data (){
    return {
      code_status: code_status,
      similar_status: similar_status,
    }
  },
  // created: function () {
    // this.$axios
    //   .get("http://127.0.0.1:8000/blog")
    //   .then((Response) => this.datas = Response.data)
    //   .catch((Error) => {
    //     console.log(Error);
    //   });
  // },
  mounted(){
    const paramOfUrl = window.location.search;
    const param = new URLSearchParams(paramOfUrl);
    console.log(param.get("mall_id"))
    difftimeH = new Date(param.get("timestamp")*1).getHours()
    difftimeM = new Date(param.get("timestamp")*1).getMinutes()
    toggle = document.querySelector(".toggleSwitch");
    toggle_2 = document.querySelector(".toggleSwitch_2");
  },
  methods: {
    timenow: function(){
      const timeH = new Date(new Date().getTime()).getHours()
      const tiemM = new Date(new Date().getTime()).getMinutes()
      console.log(difftimeH, difftimeM)
      if (timeH - difftimeH >= 2 && tiemM >= difftimeM){
        console.log(time - difftime)
        alert('요청시간이 만료되었습니다')
        window.location.reload()
      } else{
        return true
      }
    },
    similar: function(event){
      similar_status = event
      console.log('similar '+event)
      // this.timenow()
    },
    code: function(event){
      code_status = event
      console.log('code '+event)
    },
    click_script: function(event){
      toggle_2.classList.toggle('active')
      if (toggle_2.classList.length == 1){
        console.log('toggle_2 off')
      } else if (toggle_2.classList.length == 2){
        console.log('toggle_2 on')
        if (code_status == 'on' && similar_status == 'on'){
          console.log('code on, similar on')
        } else if (code_status =='on'){
          console.log('code on')  
        } else if (similar_status == 'on'){
          console.log('similar on')  
        }
      }
    },
    click_toggle: function(event){
      toggle.classList.toggle('active')
      if (toggle.classList.length == 1){
        console.log('toggle off')
      } else if (toggle.classList.length == 2){
        console.log('toggle on')
      }
    }
  }
}
</script>