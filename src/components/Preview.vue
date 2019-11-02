<template>
  <div>
    <ul>
      <li v-for="(gif,index) in gifs" v-bind:key="index">
        <img :src="gif.images.fixed_height.url" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["gifs"]
};
</script>

<style>
li {
  list-style: none;
  display: inline-flex;
  margin-left: 10px;
  align-items: center;
}
</style>
