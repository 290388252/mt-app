<template>
    <div class="m-menu">
      <dl class="nav" @mouseleave="mouseLeave()">
        <dt>全部分类</dt>
        <dd v-for="(item,idx) in menu" :key="idx" @mouseenter="hover($event)">
          <i :class="item.type"/>{{item.title}}<span class="arrow"/>
        </dd>
      </dl>
      <div class="detail" v-if="kind" @mouseenter="sover()" @mouseleave="sout()">
        <template v-for="(item, idx) in curDetail">
          <h4 :key="idx">{{item.title}}</h4>
          <span v-for="(items) in item.child">{{items}}</span>

        </template>
      </div>
    </div>
</template>

<script>
    export default {
        name: "Emenu",
      data() {
          return {
            kind:'',
            _timer:'',
            menu:[{type:'food',title:'美食',child:[{title:'美食',child:['代金券','甜点饮品','火锅']}]},
              {type:'takeout',title:'外卖',child:[{title:'外卖',child:['代金券','甜点饮品','火锅']}]},
              {type:'hotel',title:'酒店',child:[{title:'酒店',child:['代金券','甜点饮品','火锅']}]}]
          }
      },
      computed:{
          curDetail() {
            return this.menu.filter(item => item.type === this.kind)[0].child;
          }
      },
      methods: {
        mouseLeave() {
          this._timer = setTimeout(() => {
            this.kind = '';
          }, 150)
        },
        hover(e) {
          this.kind = e.target.querySelector('i').className
        },
        sover() {
          clearInterval(this._timer);
        },
        sout() {
          this.kind = '';
        }
      }
    }
</script>

<style lang="css">
</style>
