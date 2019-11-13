<template>
  <div class="hello">
    <set-tree :treeData="dataInof"
    :triangle="true"
    :checkbox="true"
    ></set-tree>
  <!-- treeData:传入数据；
    triangle:三角显示（true开启/false关闭）--选填，默认关闭
    checkbox:复选框显示（true开启/false关闭）--选填，默认关闭 -->
  </div>
</template>

<script>
import setTree from './setTree'

export default {
  name: 'HelloWorld',
  components: {
    setTree
  },
  data () {
    return {
      dataInof: [
        {
          title: 'a1',
          id: 1,
          list: [
            {
              title: 'b1',
              id: 4,
              list: [
                {
                  title: 'c1',
                  id: 13,
                  list: [
                    {
                      title: 'd1',
                      id: 40
                    },
                    {
                      title: 'd2',
                      id: 41,
                      list: [
                        {
                          title: 'd1',
                          id: 42
                        },
                        {
                          title: 'd2',
                          id: 43
                        }
                      ]
                    }
                  ]
                },
                {
                  title: 'c2',
                  id: 14
                },
                {
                  title: 'c3',
                  id: 15
                }
              ]
            },
            {
              title: 'b2',
              id: 5,
              list: [
                {
                  title: 'c1',
                  id: 16
                },
                {
                  title: 'c2',
                  id: 17
                },
                {
                  title: 'c3',
                  id: 18
                }
              ]
            },
            {
              title: 'b3',
              id: 6,
              list: [
                {
                  title: 'c1',
                  id: 19
                },
                {
                  title: 'c2',
                  id: 20
                },
                {
                  title: 'c3',
                  id: 21
                }
              ]
            }
          ]
        },
        {
          title: 'a2',
          id: 2,
          list: [
            {
              title: 'b1',
              id: 7,
              list: [
                {
                  title: 'c1',
                  id: 22
                },
                {
                  title: 'c2',
                  id: 23
                },
                {
                  title: 'c3',
                  id: 24
                }
              ]
            },
            {
              title: 'b2',
              id: 8,
              list: [
                {
                  title: 'c1',
                  id: 25
                },
                {
                  title: 'c2',
                  id: 26
                },
                {
                  title: 'c3',
                  id: 27
                }
              ]
            },
            {
              title: 'b3',
              id: 9,
              list: [
                {
                  title: 'c1',
                  id: 28
                },
                {
                  title: 'c2',
                  id: 29
                },
                {
                  title: 'c3',
                  id: 30
                }
              ]
            }
          ]
        },
        {
          title: 'a3',
          id: 3,
          list: [
            {
              title: 'b1',
              id: 10,
              list: [
                {
                  title: 'c1',
                  id: 31
                },
                {
                  title: 'c2',
                  id: 32
                },
                {
                  title: 'c3',
                  id: 33
                }
              ]
            },
            {
              title: 'b2',
              id: 11,
              list: [
                {
                  title: 'c1',
                  id: 34
                },
                {
                  title: 'c2',
                  id: 35
                },
                {
                  title: 'c3',
                  id: 36
                }
              ]
            },
            {
              title: 'b3',
              id: 12,
              list: [
                {
                  title: 'c1',
                  id: 37
                },
                {
                  title: 'c2',
                  id: 38
                },
                {
                  title: 'c3',
                  id: 39
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
</script>

<style>
  .checkBox{
      padding: 3px;
      float: left;
  }
  .checkBox div{
      width: 10px;
      height: 10px;
      font-size: 12px;
      line-height: 10px;
      text-align: center;
      color: #fff;
      background-color: #fff;
      border: 1px solid #c9c9c9;
      border-radius: 2px;
  }
  .checkBox .ba{
    background-color: #409eff;
    border-color: #409eff;
  }
  .hello{
    width: 500px;
    padding: 40px;
    text-align: left;
    border: 1px solid #ebebeb;
    border-radius: 3px;
    transition: .2s;
  }
  .hello:hover{
    box-shadow: 0 0 8px 0 rgba(232, 237, 250, .6), 0 2px 4px 0 rgba(232, 237, 250, .5)
  }
  .pr{
    position: relative;
  }
  .box{
    height: 20px;
    line-height: 20px;
    border-radius: 1px;
    position: relative;
  }
  .box:hover{
    background-color: #f0f7ff;
  }
  .b{
    width: 0;
    height: 0;
    border-right: 5px solid #fff;
    border-left: 5px solid #fff;
    border-bottom: 5px solid #c0c4cc;
    position: absolute;
    top: 7px;
    left: 0;
  }
  .c{
    width: 0;
    height: 0;
    border-top: 5px solid #c0c4cc;
    border-right: 5px solid #fff;
    border-left: 5px solid #fff;
    position: absolute;
    bottom: 7px;
    left: 0;
  }
  .b2{
    left: 10px;
  }
</style>
