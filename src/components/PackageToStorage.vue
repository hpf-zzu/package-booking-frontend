<template>
    <div>
        <h2>包裹入库</h2>
  <a-form
    :form="form"
    @submit="handleSubmit"
  >
    <a-form-item
      label="运单号："
      :label-col="{ span: 5 }"
      :wrapper-col="{ span: 12 }"
    >
      <a-input
        v-decorator="[
          'waybillNum',
          {rules: [{ required: true, message: '运单号不能为空' }]}
        ]"
         placeholder="请填写你的运单号"
      />
    </a-form-item>

     <a-form-item
      label="收件人："
      :label-col="{ span: 5 }"
      :wrapper-col="{ span: 12 }"
    >
      <a-input
        v-decorator="[
          'recipients',
          {rules: [{ required: true, message: '收件人的姓名不能为空' }]}
        ]"
        placeholder="请填写收件人的姓名"
      />
    </a-form-item>

     <a-form-item
      label="电话："
      :label-col="{ span: 5 }"
      :wrapper-col="{ span: 12 }"
    >
      <a-input
        v-decorator="[
          'phoneNum',
          {rules: [{ required: true, message: '联系人电话不能为空' }]}
        ]"
        placeholder="请填写电话"
      />
    </a-form-item>

     <a-form-item
      label="重量："
      :label-col="{ span: 5 }"
      :wrapper-col="{ span: 12 }"
    >
      <a-input
        v-decorator="[
          'weight',
          {rules: [{ required: true, message: '包裹重量不能为空' }]}
        ]"
        placeholder="请填写包裹重量"
      />
    </a-form-item>
   
    <a-form-item
      :wrapper-col="{ span: 12, offset: 5 }"
    >
      <a-button
        type="primary"
        html-type="submit"
      >
        Submit
      </a-button>
    </a-form-item>
  </a-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      formLayout: 'horizontal',
      form: this.$form.createForm(this),
    };
  },
  methods: {
    handleSubmit (e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
           this.$store.dispatch("postPackages",values);
        }
      });
    },
  },
};
</script>
