<template>
  <b-modal id="registerModalForPatient">
    <template slot="modal-header">
      <h5>收费</h5>
    </template>
    <b-form>
      <b-row>
        <b-col md="2"></b-col>
        <b-col md="8">
          <b-form-group
            label="收费方式"
            label-for="payMode"
            :label-cols="4"
            :horizontal="true">
            <b-form-select id="payMode"
                           :plain="true"
                           v-model="payModeId"
                           :options="options"
            >
            </b-form-select>
          </b-form-group>
        </b-col>
      </b-row>
      <b-row>
        <b-col md="2"></b-col>
        <b-col md="8">
          <b-form-group label-for="totalCost" label="应收金额">
            <b-form-input id="totalCost" type="text" class="form-control-success" :value="totalCost" disabled></b-form-input>
          </b-form-group>
        </b-col>
      </b-row>
    </b-form>
    <!--成功按钮 提交添加或编辑 判断是否变化-->
    <template slot="modal-footer">
      <b-button variant="success" class="btn-pill" @click="register">缴费</b-button>
      <b-button variant="danger" class="btn-pill" @click="cancel">取消</b-button>
    </template>
  </b-modal>
</template>

<script>
    export default {
        name: "registerModalForPatient",
        props: {
          totalCost: {
            type: Number,
            default: 0,
          },
        },
        data: () => {
          return {
            payModeId: 51,
            options: [
              {text: '现金', value: 51},
              {text: '医保卡', value: 52},
              {text: '银行卡', value: 53},
              {text: '信用卡', value: 54},
              {text: '微信', value: 55},
              {text: '支付宝', value: 56},
              {text: '云闪付', value: 57},
              {text: '其它', value: 58},
            ],
          }
        },
        methods: {
          register(){
            this.$bvModal.hide('registerModalForPatient');
            this.$emit('register', this.payModeId);
          },
          cancel(){
            this.$bvModal.hide('registerModalForPatient');
          },
        }
    }
</script>

<style scoped>

</style>
