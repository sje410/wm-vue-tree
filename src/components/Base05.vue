<template>
  <div>
    <h3 class="tree-demo-title-h3">节点的样式</h3>
    <p>可自行设置节点的默认样式和选中的样式</p>
    <BaseCard>
      <template v-slot:header>
        <div class="component-wrapper">
          <wm-vue-tree
            :data="data"
            direction="horizontal"
            show-collapsable
            default-expand-all
            :label-class-name="renderLabelClass"
            :current-lable-class-name="renderCurrentClass"
          ></wm-vue-tree>
        </div>
      </template>
      <template v-slot:description>
        通过
        <code>label-class-name</code> 设置节点的样式，支持字符和函数方式。通过
        <code>current-lable-class-name</code>
        设置当前节点选中的样式，支持字符和函数方式。
      </template>
      <template>
        <pre
          class="language-css"
          v-html="Prism.highlight(content, Prism.languages.html, 'html')"
        ></pre>
      </template>
    </BaseCard>
  </div>
</template>
<script>
import mixins from "./mixins";
export default {
  mixins: [mixins],
  data() {
    return {
      data: [],
      content: `<wm-vue-tree
  :data="data"
  direction="horizontal"
  show-collapsable
  default-expand-all
  :label-class-name="renderLabelClass"
  :current-lable-class-name="renderCurrentClass"
  /> \n
<script>
  export default {
    data () {
      return {
        data: [{
          label: '公司',
          children: [{
            label: '产品研发部',
            children: [{
              label: '研发-前端',
            }, {
              label: '研发-后端',
            }]
          }, {
            label: '销售部',
            children: [{
                label: '销售一部',
              },{
                label: '销售二部',
              },{
                label: '销售三部',
              }
            ]
          },{
            label: '财务部'
          }]
        }]
      }
    },
    mounted ()
{
    this.init()
  },
    methods: {
      renderLabelClass (node) {
        return 'label-class-blue'
      },
      renderCurrentClass (node) {
        return 'label-bg-blue'
      },
      init() {
          this.data.push({
        name: '公司',
        type: 4,
        status: 1
      },{
        name: '公司',
      },{
        name: '公司',
        children: [{
          name: '产品研发部',
          children: [{
            name: '研发-前端',
          }, {
            name: '研发-后端',
          }]
        }]
      })
      }
    }
  }
<\/script>
<style>
.label-bg-blue{
  background: #1989fa;
  color: #fff;
}
.icon-class-blue{
  border-color: darkred;
}
</style>
`
    };
  },
  methods: {
    renderLabelClass(node) {
      return "label-class-blue";
    },
    renderCurrentClass(node) {
      return "label-bg-blue";
    },
    renderIconClass () {
      return 'icon-class-blue'
    },
  }
};
</script>

<style>

.label-bg-blue {
  background: #1989fa;
  color: #fff;
}
</style>
