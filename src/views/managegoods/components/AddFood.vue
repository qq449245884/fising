<template>
  <div class="condition-container">
    <el-dialog
      title="添加饲料"
      @close="closeDialog"
      @open="handleOpen"
      top="2vh"
      show="show"
      width="550px"
      :visible.sync="visible">
      <div class="form-wrapper">
        <el-form ref="addForm" :model="addForm" :rules="rules" :inline="true" size="mini" label-position='top' label-width="80px">
          <el-form-item label="饲料种类:">
            <el-select v-model="addForm.type" placeholder="请选择渔药种类">
              <el-option label="区域一" value="shanghai"></el-option>
              <el-option label="区域二" value="beijing"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="饲料名称:">
            <el-input placeholder="请输入渔药名称" v-model="addForm.type"/>
          </el-form-item>
          <el-form-item label="供应单位:">
            <el-input placeholder="请输入供应单位" v-model="addForm.type"/>
          </el-form-item>
          <el-form-item label="规格:">
            <div class="form-inline">
              <el-input class='input' placeholder="请输入" v-model="addForm.type"/>
              <el-select v-model="addForm.type" placeholder="选择单位">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
              <span>kg</span>
            </div>
          </el-form-item>
          <el-form-item label="联系人:">
            <el-input placeholder="请输入联系人姓名" v-model="addForm.type"/>
          </el-form-item>
          <el-form-item label="采购数量:">
            <div class="form-inline">
              <el-input class='input' placeholder="请输入" v-model="addForm.type"/>
              <el-input placeholder="计算重量" v-model="addForm.type"/>
              <span>kg</span>
            </div>
          </el-form-item>
          <el-form-item label="联系电话:">
            <el-input placeholder="请输入联系人电话" v-model="addForm.type"/>
          </el-form-item>
          <el-form-item label="总价:">
            <div class="form-inline">
              <el-input placeholder="总价" v-model="addForm.type"/>
              <el-input placeholder="计算单价" v-model="addForm.type"/>
              <span>元</span>
            </div>
          </el-form-item>
          <el-form-item label="购买日期:">
            <el-date-picker type="date" placeholder="选择日期" v-model="addForm.type" />
          </el-form-item>
          <el-form-item />
          <el-form-item align="right" style="margin-top:10px;width:100%">
            <el-button type="primary" @click="handleSave">保存</el-button>
            <el-button @click="closeDialog">取消</el-button>
          </el-form-item>
        </el-form>  
      </div>
    </el-dialog>
  </div>
</template>
<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false
    },
    list: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  data () {
    return {
      visible: this.show,
      addForm: {
        type: null
      },
      rules: {}
    }
  },
  methods: {
    handleOpen () {},
    closeDialog () {
      this.$emit('update:show', false);
      this.$emit('handleClose');
    },
    // 保存
    handleSave () {
      this.$emit('update:show', false)
    }
  },
  watch: {
    show () {
      this.visible = this.show;
    }
  }
}
</script>

<style scope lang='scss'>
  .form-wrapper{
    display: flex;
    justify-content: center;
    padding-left: 10px;
    box-sizing: border-box;
    width: 100%;
    .el-form-item {
      width: 180px;
    }
    .el-date-editor--date{
      width: 180px;
    }
    .el-input{
      width: 210px;
    }
    .el-select{
      width: 180px;
    }
    
  }
  .el-form-item:nth-child(2n+1){
    margin-right: 60px;
  }
  .form-inline{
    display: flex;
    width: 220px;
    .el-input{
      width: 120px !important;
      margin-right: 15px;
    }
    .el-select{
      .el-input{
        width: 105px !important;
        margin-right: 15px;
      }
    }
  }
</style>