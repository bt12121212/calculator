<template>
  <el-container direction="vertical">
    <el-input v-model="expression" placeholder="Enter your expression here..."></el-input>
    <el-button type="primary" @click="calculate">Calculate</el-button>
    <el-divider></el-divider>
    <el-list>
      <el-list-item v-for="(item, index) in history" :key="index">{{ item }}</el-list-item>
    </el-list>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      expression: '',
      history: []
    };
  },
  methods: {
    calculate() {
      try {
        const result = eval(this.expression);
        this.history.push(`${this.expression} = ${result}`);
        this.expression = '';
      } catch (error) {
        console.log('Invalid expression');
      }
    }
  }
};
</script>