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
              <p style="font-weight: 900;">SET 1</p>
              <h2>장바구니 페이지에서 유사상품 추천하기</h2>
              <span>이 기능을 활성화하면 고객이 장바구니에서 관련상품을 확인할 수 있습니다.</span>
            </div>
            <div style="zoom: 2; margin: auto;">
              <b-form-checkbox
                id="cart_checkbox"
                v-model="cart_status"
                name="cart_checkbox"
                value="on"
                unchecked-value="off"
              ></b-form-checkbox>
              <div style="font-size: 10px">State: <strong>{{ cart_status }}</strong></div>
            </div>
          </div>
          
          <div style="display: flex; padding: 30px 40px;">
            <div style="width: 80%">
              <p style="font-weight: 900;">SET 2</p>
              <h2>아이템 리스트 페이지에서 유사상품 추천하기</h2>
              <span>이 기능을 활성화하면 고객이 아이템 리스트 페이지에서 관련상품을 확인할 수 있습니다.</span>
            </div>
            <div style="zoom: 2; margin: auto;">
              <b-form-checkbox
                id="item_list_checkbox"
                v-model="item_list"
                name="item_list_checkbox"
                value="on"
                unchecked-value="off"
              ></b-form-checkbox>
              <div style="font-size: 10px">State: <strong>{{ item_list }}</strong></div>
            </div>
          </div>
          
          <div style="display: flex; padding: 30px 40px;">
            <div style="width: 80%">
              <p style="font-weight: 900;">SET 3</p>
              <h2>아이템 상세 페이지에서 유사상품 추천하기</h2>
              <span>이 기능을 활성화하면 고객이 아이템 상세 페이지 에서 관련상품을 확인할 수 있습니다.</span>
            </div>
            <div style="zoom: 2; margin: auto;">
              <b-form-checkbox
                id="item_detail_checkbox"
                v-model="item_detail"
                name="item_detail_checkbox"
                value="on"
                unchecked-value="off"
              ></b-form-checkbox>
              <div style="font-size: 10px">State: <strong>{{ item_detail }}</strong></div>
            </div>
          </div>

        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
var cart_status = 'off'
var item_list = 'off'
var item_detail = 'off'
export default {
  name: 'IndexPage',
    data() {
    return {
      cart_status: cart_status,
      item_list: item_list,
      item_detail: item_detail
    }
  }
}
</script>
