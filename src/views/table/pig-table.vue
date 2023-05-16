<template>
  <div class="app-container">
    <div class="filter-container">
      <el-button
        class="filter-item"
        style="margin-left: 10px;"
        type="primary"
        icon="el-icon-edit"
        @click="handleCreate"
      >
        添加
      </el-button>
    </div>

    <el-table
      v-loading="listLoading"
      :data="list"
      border
      fit
      highlight-current-row
      style="width: 100%"
    >

      <el-table-column
        align="center"
        label="编号"
        width="80"
      >
        <template slot-scope="{row}">
          <span>{{ row.id }}</span>
        </template>
      </el-table-column>
      <el-table-column
        width="180px"
        align="center"
        label="猪圈名称"
      >
        <template slot-scope="{row}">
          <span>{{ row.name }}</span>
        </template>
      </el-table-column>
      <el-table-column
        width="120px"
        align="center"
        label="摄像头信息"
      >
        <template slot-scope="{row}">
          <span>{{ row.cameraInfo }}</span>
        </template>
      </el-table-column>
      <el-table-column
        width="120px"
        align="center"
        label="设备信息"
      >
        <template slot-scope="{row}">
          <span>{{ row.deviceInfo }}</span>
        </template>
      </el-table-column>
      <el-table-column
        align="center"
        label="操作"
        width="120"
      >
        <template slot-scope="{row}">
          <el-button
            v-if="row.edit"
            type="success"
            size="small"
            icon="el-icon-circle-check-outline"
            @click="confirmEdit(row)"
          >
            Ok
          </el-button>
          <el-button
            v-else
            type="primary"
            size="small"
            icon="el-icon-edit"
            @click="row.edit=!row.edit"
          >
            Edit
          </el-button>
        </template>
      </el-table-column>
    </el-table>

    <el-dialog
      title="添加猪圈数据"
      :visible.sync="dialogFormVisible"
    >
      <el-form
        ref="dataForm"
        :model="addForm"
        label-width="80px"
      >
        <el-form-item label="猪圈名称">
          <el-input v-model="addForm.name" />
        </el-form-item>
        <el-form-item>
          <el-button
            type="primary"
            @click="onSubmit"
          >添加猪圈</el-button>
          <el-button @click="dialogFormVisible = false">取消</el-button>
        </el-form-item>
      </el-form>

    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'PigTable',
  data() {
    return {
      list: [{
        id: 1,
        name: 'pig1',
        cameraInfo: 'test_camera',
        deviceInfo: 'test_device'
      }],
      listLoading: false,
      dialogFormVisible: false,
      addForm: {
        id: 1,
        name: '',
        cameraInfo: '',
        deviceInfo: ''
      }
    }
  },
  methods: {

    handleCreate() {
      this.addForm = {
        id: null,
        name: '',
        cameraInfo: '',
        deviceInfo: ''
      }

      this.dialogFormVisible = true
    },
    onSubmit() {
      this.addForm.id = parseInt(Math.random() * 100) + 1024
      this.list.push(this.addForm)
      this.dialogFormVisible = false
    }

  }

}
</script>

<style>
</style>
