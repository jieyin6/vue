<template>
 <div>
     <input v-focus />
     <div v-demo="{color: 'white', text: 'text'}"></div>
     <span v-text="msg"></span>
     <span>{{msg}}</span>
     <div v-html="html"></div>
     <!--<div v-on="{ mousedowm: dothis, mouseup: dothat}"></div>-->
     <div @click="handle('ok', $event)">dianji</div>
     <div :class="{ red: isRed }"></div>
     <div :class="[class1, class2]"></div>
     <div :class="[class1,{ class2:a, class3:b }]"></div>
     <div :style="{ fontSize: size + 'px'}"></div>
     <div v-bind="{id: app, 'other': other }"></div>
     <div :text-content.prop="text"></div>
     <input v-model="some"/>
     <input v-bind:value="some" v-on:input="some = $event.target.value">
     <div v-cloak>hello</div> <!--不会显示，知道编译结束-->
     <div v-once></div>
 </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'text',
      html: '<span>nihao</span>'
    }
  },
  mounted () {
    console.log(this.$el)
  },
  methods: {
    handle (a, b) {
      console.log(a, b)
    },
    dothis () {},
    dothat () {}
  },
  directives: {
    focus: {
      inserted: function (el) {
        el.focus()
      }
    },
    demo: function (el, binding) {
      console.log(binding.value.color)
      console.log(binding.value.text)
    }
  }
}
</script>

<style>
[v-cloak]{
    display: none;
}
</style>
