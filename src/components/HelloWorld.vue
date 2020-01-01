<template>
  <div class="hello">
    <div>
      <h1>{{ arr }}</h1>
      <button @click='change_0'>push arr[3]</button>
      <button @click='change_1'>edit arr[2]</button>
      <button @click='change_2'>edit arr.length</button>
    </div>
    <div class="blank"></div>
    <div>
      <h1>My name : {{ obj.name }}</h1>
      <button
        class="long"
        @click='change_10'
      >this.obj.name = '老实敦厚的泽哥'</button>
      <div></div>
      <h1>My nickname : {{ obj.nickname }}</h1>
      <button
        class="long"
        @click='change_11'
      >this.obj.nickname = '老实敦厚的泽哥'</button>
      <div></div>
      <h1>My colleague : {{ objArr[0].name }},{{ objArr[1].name }}</h1>
      <button
        class="long"
        @click='change_12'
      >this.objArr[0].name = 'lemanzhang',this.objArr[1].name = 'bobby'</button>
    </div>
    <div>
      <h1>dataWeakSet.size : {{dataWeakSet.size}}</h1>
      <button
        class="long"
        @click='change_21'
      >dataWeakSet.add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      arr: [
        1, 2, 3
      ],
      obj: {
        name: 'zelinliu'
      },
      objArr: [
        {},
        { name: 'xixinhuang' }
      ],
      dataWeakSet: {

      }
    }
  },
  mounted() {
    this.dataWeakSet = new Set([1, 1, 2, 3, 3])
  },
  methods: {
    // 1.  Vue2.X不能检测数组的项修改（根据index）、length修改（可直接对数组重新赋值，如使用filter、map、concat、slice等方式生成新数组对其赋值）
    change_0: function () {
      this.arr.push(5)
      alert('arr : ' + this.arr)
    },
    change_1: function () {
      this.arr[2] = 5
      alert('arr : ' + this.arr)
    },
    change_2: function () {
      this.arr.length = 5
      alert('arr : ' + this.arr)
    },
    // 2.  Vue2.X不能检测对象属性的添加、删除（可直接对该对象重新赋值、修改该对象或内层对象的属性）
    change_10: function () {
      this.obj.name = '刘泽霖'
      this.obj.nickname = '老实敦厚的泽哥'
      alert('昵称叫 :' + this.obj.nickname)
      alert('真名叫 :' + this.obj.name)
    },
    change_11: function () {
      this.obj.nickname = '老实敦厚的泽哥'
      // this.$set(this.obj, 'nickname', '老实敦厚的泽哥')
      alert('昵称叫 :' + this.obj.nickname)
    },
    change_12: function () {
      this.objArr[0].name = this.objArr[0].name + 'lemanzhang'
      this.objArr[1].name = 'bobby'
      alert('My colleague :' + this.objArr[0].name + ',' + this.objArr[1].name)
    },
    change_21: function () {
      this.dataWeakSet.add(4)
      alert('dataWeakSet.size: ' + this.dataWeakSet.size)
      // this.obj = { '1': 2 }
    }
  },
  watch: {
    obj: {
      handler: function (newValue, oldValue) {
        alert('watch监听到啦！nickname叫' + JSON.stringify(newValue))
      },
      deep: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
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
div.blank {
  height: 50px;
}
button {
  height: 30px;
  width: 100px;
}
button.long {
  height: 30px;
  width: 300px;
}
</style>
