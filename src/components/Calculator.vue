<template>
  <div class="calc" :class="{backTheme2: theme === 2, backTheme3: theme === 3}">
    <div class="container">
    <h2 :class="{txtColor2: theme === 2, txtColor3: theme === 3}">calc</h2>
    <div class="theme" :class="{txtColor2: theme === 2, txtColor3: theme === 3}">
      <p class="title">THEME</p>
      <div class="toggler">
        <p class="nums-theme">
          <span @click="theme = 1">1</span>
          <span @click="theme = 2">2</span>
          <span @click="theme = 3">3</span>
          </p>
        <div class="btn" :class="{toggleBack2: theme === 2,toggleBack3: theme === 3}">
          <button :class="{circleBack2: theme === 2, circleBack3: theme === 3}"></button>
        </div>
      </div>
    </div>
    <input type="text" v-model="value"
        :class="{inputTheme2: theme === 2, inputTheme3: theme === 3}">
    <div class="keys" :class="{keysTheme2: theme === 2, keysTheme3: theme === 3}">
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('7')">7</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('8')">8</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('9')">9</button>
        <button class="delete" :class="{btnDelTheme2: theme === 2,
                                        btnDelTheme3: theme === 3 }"
                                        @click="removeChar">DEL</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('4')">4</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('5')">5</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('6')">6</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }"
                          @click="typeNum('+'); handleOperators();">+</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('1')">1</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('2')">2</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('3')">3</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }"
                          @click="typeNum('-'); handleOperators();">-</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }" @click="typeNum('.')">.</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }"
                          @click="typeNum('0'); handleOperators();">0</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }"
                          @click="typeNum('/'); handleOperators();">/</button>
        <button :class="{ btnTheme2: theme === 2,
                          btnTheme3: theme === 3 }"
                          @click="typeNum('*'); handleOperators();">&#9747;</button>
        <button class="reset" :class="{ btnResTheme2: theme === 2,
                                        btnResTheme3: theme === 3 }"
                                        @click="resetInput">Reset</button>
        <button class="equal" :class="{ btnEqTheme2: theme === 2,
                                        btnEqTheme3: theme === 3 }"
                                        @click="value.length > 0 ? equal() : ''">=</button>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      value: '',
      theme: 1,
    };
  },
  methods: {
    typeNum(num) {
      this.value += num;
    },
    removeChar() {
      this.value = this.value.substring(0, this.value.length - 1);
    },
    resetInput() {
      this.value = '';
    },
    equal() {
      try {
      // eslint-disable-next-line no-eval
        this.value = eval(this.value).toString();
      } catch (error) {
        this.value = 'ERROR';
      }
    },
    handleOperators() {
      const plus = this.value.indexOf('+');
      const minus = this.value.indexOf('-');
      const divide = this.value.indexOf('/');
      const display = this.value.indexOf('*');
      if (plus === 0 || minus === 0 || display === 0 || divide === 0) {
        this.value = '';
      }
    },
  },
};
</script>
