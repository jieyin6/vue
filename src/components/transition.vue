<template>
  <div>
      <button @click="show = !show">toggle</button>
      <transition name="slide-fade" :duration="1000">
        <p v-if="show">hello</p>
      </transition>
      <transition @before-enter="beforeEnter"
                  @enter="enter"
                  @leave="leave">
        <p v-if="show">ha</p>
      </transition>
      <button @click="add">add</button>
      <transition-group name="list">
          <span v-for="item in list" :key="item">{{item}}</span>
      </transition-group>
      <transition enter-active-class="animated fadeIn" leave-active-class="animated rollIn">
          <p v-if="show">animate</p>
      </transition>
  </div>
</template>

<script>
export default {
  data () {
    return {
      show: true,
      list: [1, 2, 3, 4],
      num: 10
    }
  },
  methods: {
    beforeEnter (el) {
      el.style.opacity = 0
    },
    enter (el, done) {
      el.style.opacity = 1
      done()
    },
    leave (el, done) {
      el.style.opacity = 0
      done()
    },
    randomIndex () {
      return Math.floor(Math.random() * this.list.length)
    },
    add () {
      this.list.splice(this.randomIndex(), 0, this.num++)
    }
  }

}
</script>

<style>
.slide-fade-enter-active{
    transition: all .3s ease;
}
.slide-fade-leave-active{
    transition: all .8s cubic-bezier(1.0,0.5,0.8,1.0);
}
.slide-fade-enter,.slide-fade-leave-to{
    transform: translateX(10px);
    opacity: 0;
}
.list-enter-active,.list-leave-active{
  transition: all 1s;
}
.list-enter,.list-leave-to{
    opacity: 0;
    transform: translateY(30px);
}
</style>
