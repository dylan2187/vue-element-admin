<template>
  <div class="app-container">
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
      listLoading: false
    }
  }

}
</script>

<style>
</style>
