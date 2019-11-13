<template>
  <div class="tree">
    <div v-for="(item,index) in treeData" :key="index">
      <div class="box" :style="{'padding-left': item.layer*10+'px'}" @click.stop="doClick(index)">
        <span v-if="item.list&&item.triangle" :class="item.flag?'b':'c'" :style="{'left': item.layer*10-10+'px'}"></span>
        <div v-if="item.checkbox" class="checkBox" @click.stop="doSelect(index)">
          <div :class="item.check?'ba':''">{{item.check === 2?'-':'✓'}}</div>
        </div>
        <span>{{item.title}}</span>
      </div>
      <div v-if="item.list">
        <tree v-if="item.flag"
        :treeData="item.list"
        :treeSerial="index"
        :defaultExpanded="defaultExpanded"
        :defaultChecked="defaultChecked"
        @getSelect="setSelect"></tree>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'tree',
  props: [
    'treeData',
    'treeSerial',
    'defaultExpanded',
    'defaultChecked'
  ],
  mounted () {
    // console.log(this.defaultExpanded)
    if (this.defaultExpanded && this.defaultExpanded[0]) {
      this.doExpanded(this.treeData, this.defaultExpanded)
    }
  },
  methods: {
    doClick (i) {
      this.treeData.map((item, index) => {
        if (index === i) {
          item.flag = !item.flag
          if (item.list) {
            let layer = item.layer + 1
            let triangle = item.triangle
            let checkbox = item.checkbox
            item.list.map((item, index) => {
              item.layer = layer
              item.triangle = triangle
              item.checkbox = checkbox
            })
            item.list.push()
          }
        }
      })
      // console.log(this.treeData)
    },
    setSelect: function (serial, val) {
      let checkOne = true
      let checkTwo = true
      let checkThree = true
      this.treeData.map((item, index) => {
        if (index === serial) {
          item.check = val
        }
        item.check ? checkOne = false : checkTwo = false
        item.check === 2 ? checkThree = false : item.check = item.check
      })
      this.$emit('getSelect', this.treeSerial, 2)
      if (checkOne) this.$emit('getSelect', this.treeSerial, 0)
      if (checkTwo && checkThree) this.$emit('getSelect', this.treeSerial, 1)
      this.treeData.push()
    },
    doSelect: function (i) {
      let value
      let checkOne = true
      let checkTwo = false
      this.treeData[i].check === 1 ? value = 0 : value = 1
      this.treeData.map((item, index) => {
        if (index === i) {
          item.check = value
          this.doCount(item, value)
        }
        item.check ? checkOne = false : checkTwo = true
      })
      this.$emit('getSelect', this.treeSerial, 2)
      if (checkOne) this.$emit('getSelect', this.treeSerial, 0)
      if (!checkTwo) this.$emit('getSelect', this.treeSerial, 1)
      this.treeData.push()
    },
    doCount: function (item, value) {
      if (item.list) {
        item.list.map((item, index) => {
          item.check = value
          if (item.list) this.doCount(item, value)
        })
        item.list.push()
      }
    },
    doExpanded: function (treeData, defaultExpanded) {
      // console.log(defaultExpanded)
      treeData.map((item, index) => {
        if (defaultExpanded.indexOf(item.id) + 1) {
          let id = item.id
          setTimeout(() => {
            defaultExpanded.map((item) => {
              if (id === item) {
                this.doClick(item - 1)
              }
            })
            let val = defaultExpanded.indexOf(id)
            defaultExpanded.splice(val, 1)
            console.log(item.list)
            console.log(defaultExpanded.length)
            if (item.list && defaultExpanded.length - 1 === index) {
              this.doExpanded(item.list, defaultExpanded)
            }
          }, 10)
        }
      })
    }
  }
}
</script>

<style>
</style>
