<template>
  <div id="vue">
    <transition-group class="carousel" name="list-complete" tag="ul">
      <li class="item" v-for="item in items" :key="item">
        {{ item }}
      </li>
    </transition-group>

    <button @click.prevent="next">next</button>

    <button @click.prevent="prev">prev</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      items: [1, 2, 3, 4, 5],
    };
  },
  methods: {
    next() {
      const item = this.items[0];

      this.items.push(item);
      setTimeout(() => {
        this.items.splice(0, 1)[0];
      });
    },
    prev() {
      const item = this.items[this.items.length - 1];

      this.items.unshift(item);
      setTimeout(() => {
        this.items.splice(this.items.length - 1, 1)[0];
      });
    },
  },
};
</script>

<style lang="scss">
$timing: 0.5s;
$easing: ease-in-out;

.carousel {
  width: 360px;
  white-space: nowrap;
  dir: rtl;
  padding-left: 0;
}

.list-complete-item {
  transition: all 1s;
  display: inline-block;
  margin-right: 10px;
}

.list-complete-enter,
.list-complete-leave-to {
  opacity: 0;
}

.list-complete-leave-active {
  position: absolute;
}

.item {
  display: inline-block;
  height: 200px;
  width: 100px;
  background: pink;
  border: 10px solid black;
  transition: all $timing $easing;
}
</style>
