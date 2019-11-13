<template>
  <div class="set">
    <tree :treeData="treeData"
    :treeSerial="1"
    :defaultExpanded="defaultExpanded"
    :defaultChecked="defaultChecked"
    ></tree>
  </div>
</template>

<script>
import tree from './tree'

export default {
  name: 'setTree',
  props: [
    'treeData',
    'triangle',
    'checkbox',
    'defaultExpanded',
    'defaultChecked'
  ],
  components: {
    tree
  },
  mounted () {
    // console.log(this.treeData)
    this.treeData.map((item, index) => {
      item.layer = 1
      item.triangle = this.triangle
      item.checkbox = this.checkbox
    })
    this.treeData.push()
  }
}
</script>

<style>

</style>
