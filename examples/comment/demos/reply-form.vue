<template>
  <t-comment avatar="https://tdesign.gtimg.com/site/avatar.jpg">
    <template #content>
      <div class="form-container">
        <t-textarea v-model="replyData" placeholder="请输入内容" />
        <t-button class="form-submit" @click="submitReply">回复</t-button>
      </div>
    </template>
  </t-comment>
</template>

<script>
import { defineComponent, ref } from 'vue';
import { NotifyPlugin } from 'tdesign-vue-next';

export default defineComponent({
  setup() {
    const replyData = ref('');

    const submitReply = () => {
      NotifyPlugin.info({
        title: '回复内容',
        content: replyData.value,
        duration: 3000,
      });
    };

    return {
      replyData,
      submitReply,
    };
  },
});
</script>

<style lang="less" scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  .form-submit {
    margin-top: 8px;
  }
}
</style>
