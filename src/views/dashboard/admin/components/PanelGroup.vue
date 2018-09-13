<template>
  <el-row :gutter="40" class="panel-group">
  <h3> Rekapitulasi Perolehan Caleg </h3>
    <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-icon-wrapper icon-people">
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">/TPS</div>
          <count-to :start-val="10" :end-val="102400" :duration="2600" class="card-panel-num"/>
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-icon-wrapper icon-people">
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">/Kabupaten</div>
          <count-to :start-val="10" :end-val="81212" :duration="3000" class="card-panel-num"/>
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-icon-wrapper icon-people">
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">/Kecamatan</div>
          <count-to :start-val="10" :end-val="9280" :duration="3200" class="card-panel-num"/>
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-icon-wrapper icon-people">
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">/Kelurahan</div>
          <count-to :start-val="10" :end-val="13600" :duration="3600" class="card-panel-num"/>
        </div>
      </div>
    </el-col>

  <br>
  <h3> Cari Perolehan Caleg </h3>
  <form
            id="app"
            @submit="checkForm"
            action="https://vuejs.org/"
            method="post"
            >
            
    <el-col :xs="12" :sm="12" :lg="4" class="card-panel-col">
              <p>
              <label for="tps">Saring:</label>
              <select
                id="tps"
                v-model="tps"
                name="tps"
              >
                <option>TPS</option>
                <option>Kabupaten</option>
                <option>Kecamatan</option>
                <option>Partai Politik</option>
              </select>
              </p>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="10" class="card-panel-col">
      <el-col :xs="12" :sm="12" :lg="8" class="card-panel-col"><p>
      <p>
      <label for="kab">Pilih Parpol:</label>
      <select
        id="kab"
        v-model="kab"
        name="kab"
      >
        <option>PDIP</option>
        <option>Demokrat</option>
        <option>Nasdem</option>
        <option>PKS</option>
        <option>Gerindra</option>
      </select>
      </p>
      </el-col>
      <el-col :xs="12" :sm="12" :lg="4" class="card-panel-col">
      <p>
      <input
        type="submit"
        value="Cari"
      >
    </p>
    </el-col>
  </el-col>
  </form>
  </el-row>


</template>

<script>
import CountTo from 'vue-count-to'

export default {
  components: {
    CountTo
  },
  methods: {
    handleSetLineChartData(type) {
      this.$emit('handleSetLineChartData', type)
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.panel-group {
  margin-top: 18px;
  .card-panel-col{
    margin-bottom: 32px;
  }
  .card-panel {
    height: 108px;
    cursor: pointer;
    font-size: 12px;
    position: relative;
    overflow: hidden;
    color: #666;
    background: #fff;
    box-shadow: 4px 4px 40px rgba(0, 0, 0, .05);
    border-color: rgba(0, 0, 0, .05);
    &:hover {
      .card-panel-icon-wrapper {
        color: #fff;
      }
      .icon-people {
         background: #40c9c6;
      }
      .icon-people {
        background: #36a3f7;
      }
      .icon-form {
        background: #f4516c;
      }
      .icon-shoppingCard {
        background: #34bfa3
      }
    }
    .icon-people {
      color: #40c9c6;
    }
    .icon-people {
      color: #36a3f7;
    }
    .icon-form {
      color: #f4516c;
    }
    .icon-shoppingCard {
      color: #34bfa3
    }
    .card-panel-icon-wrapper {
      float: left;
      margin: 14px 0 0 14px;
      padding: 16px;
      transition: all 0.38s ease-out;
      border-radius: 6px;
    }
    .card-panel-icon {
      float: left;
      font-size: 48px;
    }
    .card-panel-description {
      float: right;
      font-weight: bold;
      margin: 26px;
      margin-left: 0px;
      .card-panel-text {
        line-height: 18px;
        color: rgba(0, 0, 0, 0.45);
        font-size: 16px;
        margin-bottom: 12px;
      }
      .card-panel-num {
        font-size: 20px;
      }
    }
  }
}
</style>
