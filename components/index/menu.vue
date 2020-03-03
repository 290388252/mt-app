<template>
    <div class="m-menu">
      <dl class="nav">
        <dt>全部分类</dt>
        <dd v-for="(item,idx) in menu" :key="idx">
          <i :class="item.type"/>{{item.title}}<span class="arrow"/>
        </dd>
      </dl>
    </div>
</template>

<script>
    export default {
        name: "Emenu",
      data() {
          return {
            menu:[{type:'food',title:'美食'},
              {type:'takeout',title:'外卖'},
              {type:'food',title:'美食'}]
          }
      }
    }
</script>

<style lang="css">
</style>
