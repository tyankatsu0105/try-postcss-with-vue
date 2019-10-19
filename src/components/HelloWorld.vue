<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>色が変わる</p>

    <label for="themeSwitcher">
      カラーテーマ選択
      <select name="themeSwitcher" id="themeSwitcher" ref="themeSwitcher">
        <option value="auto">設定無し</option>
        <option value="light">Lightモード</option>
        <option value="dark">Darkモード</option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  mounted(){
    const themeSwitcher = this.$refs.themeSwitcher;
    const html = document.documentElement;

    themeSwitcher.addEventListener('change', () => {
      if (themeSwitcher.value === 'auto') {
        html.classList.remove('is-dark', 'is-light')
      } else if (themeSwitcher.value === 'light') {
        html.classList.add('is-light')
        html.classList.remove('is-dark')
      } else if (themeSwitcher.value === 'dark') {
        html.classList.add('is-dark')
        html.classList.remove('is-light')
      }
})
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
