<template lang="html">

  <div>

    <section class="markdown">
      <h1>InputNumber 数字输入框</h1>
      <p>
        通过鼠标或键盘，输入范围内的数值。
      </p>
      <h2>何时使用</h2>
      <ul>
        <p>
          当需要获取标准数值时。
        </p>
      </ul>
      <h2>组件演示</h2>
    </section>

    <v-Row :gutter="16">
      <v-Col span="12">

        <code-box
          title="基本"
          describe="数字输入框。"
        >
          <v-input-number min="1" max="10" default-value="3" :on-change="_handleChange"></v-input-number>
          <template slot="js">
          export default {
            methods: {
              _handleChange (value) {
                console.log('changed ', value)
              }
            }
          }
          </template>
        </code-box>

        <code-box
          title="不可用"
          describe="点击按钮切换可用状态。"
        >
          <v-input-number min="1" max="10" :disabled="disabled" default-value="3"></v-input-number>
          <br><br>
          <v-button @click="_toggle" type="primary">Toggle disabled</v-button>
          <template slot="js">
          export default {
            data: function() {
              return {
                disabled: true
              }
            }
            methods: {
              _toggle () {
                this.disabled = !this.disabled
              }
            }
          }
          </template>
        </code-box>

      </v-col>
      <v-Col span="12">

        <code-box
          title="三种大小"
          describe="三种大小的数字输入框，当 size 分别为 large 和 small 时，输入框高度为 32px 和 22px ，默认高度为 28px"
        >
          <v-input-number size="large" min="1" max="100000" default-value="3" :on-change="_handleChange"></v-input-number>
          <v-input-number min="1" max="100000" default-value="3" :on-change="_handleChange"></v-input-number>
          <v-input-number size="small" min="1" max="100000" default-value="3" :on-change="_handleChange"></v-input-number>
          <template slot="js">
          export default {
            methods: {
              _handleChange (value) {
                console.log('changed ', value)
              }
            }
          }
          </template>
        </code-box>

        <code-box
          title="小数"
          describe="和原生的数字输入框一样，value 的精度由 step 的小数位数决定。"
        >
          <v-input-number min="1" max="10" step="0.1"></v-input-number>
        </code-box>

      </v-col>
    </v-row>


    <api-table
      :apis='apis'
    ></api-table>

  </div>

</template>

<script>
import codeBox from '../components/codeBox'
import apiTable from '../components/apiTable'

export default {
  data: function () {
    return {
      apis: [{
          parameter: 'min',
          explain: '最小值',
          type: 'Number',
          default: '-Infinity'
        },{
          parameter: 'max',
          explain: '最大值',
          type: 'Number',
          default: 'Infinity'
        },{
          parameter: 'value',
          explain: '当前值',
          type: 'Number',
          default: '无'
        },{
          parameter: 'step',
          explain: '每次改变步数，可以为小数',
          type: 'Number',
          default: '1'
        },{
          parameter: 'defaultValue',
          explain: '初始值',
          type: 'Number',
          default: '无'
        },{
          parameter: 'onChange',
          explain: '变化回调',
          type: 'Function',
          default: '无'
        },{
          parameter: 'disabled',
          explain: '禁用',
          type: 'Boolean',
          default: 'false'
        },{
          parameter: 'size',
          explain: '输入框大小',
          type: 'String',
          default: '无'
        }
      ],
      disabled: true
    }
  },
  components: {
    codeBox,
    apiTable
  },
  methods: {
    _handleChange (value) {
      console.log('changed ', value)
    },
    _toggle () {
      this.disabled = !this.disabled
    }
  }
}
</script>