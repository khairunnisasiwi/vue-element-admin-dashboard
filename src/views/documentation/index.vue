<template>
  <div class="app-container documentation-container">
    <form
    id="app"
    @submit="checkForm"
    action="https://vuejs.org/"
    method="post"
    >
    
      <p>
      <label for="tps">TPS</label>
      <select
        id="tps"
        v-model="tps"
        name="tps"
      >
        <option>01</option>
        <option>02</option>
        <option>03</option>
      </select>
      </p>

      <p>
      <label for="kab">Kabupaten</label>
      <select
        id="kab"
        v-model="kab"
        name="kab"
      >
        <option>Kota Madya</option>
        <option>Bantul</option>
        <option>Gunung Kidul</option>
        <option>Kulon Progo</option>
        <option>Sleman</option>
      </select>
      </p>

      <p>
      <label for="kec">Kecamatan</label>
      <select
        id="kec"
        v-model="kec"
        name="kec"
      >
        <option>Depok</option>
        <option>Mlati</option>
        <option>Minggir</option>
      </select>
      </p>

      <p>
    <input
      type="submit"
      value="Simpan"
    >
  </p>
    </form>
  </div>
</template>
<script>
import DropdownMenu from '@/components/Share/dropdownMenu'

export default {
  name: 'Documentation',
  components: { DropdownMenu },
  data() {
    return {
      articleList: [
        { title: '基础篇', href: 'https://juejin.im/post/59097cd7a22b9d0065fb61d2' },
        { title: '登录权限篇', href: 'https://juejin.im/post/591aa14f570c35006961acac' },
        { title: '实战篇', href: 'https://juejin.im/post/593121aa0ce4630057f70d35' },
        { title: 'vue-admin-template 篇', href: 'https://juejin.im/post/595b4d776fb9a06bbe7dba56' },
        { title: '自行封装 component', href: 'https://segmentfault.com/a/1190000009090836' },
        { title: '优雅的使用 icon', href: 'https://juejin.im/post/59bb864b5188257e7a427c09' },
        { title: 'webpack4（上）', href: 'https://juejin.im/post/59bb864b5188257e7a427c09' },
        { title: 'webpack4（下）', href: 'https://juejin.im/post/5b5d6d6f6fb9a04fea58aabc' }
      ]
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.documentation-container {
  margin: 50px;
  .document-btn {
    float: left;
    margin-left: 50px;
    display: block;
    cursor: pointer;
    background: black;
    color: white;
    height: 60px;
    width: 200px;
    line-height: 60px;
    font-size: 20px;
    text-align: center;
  }
}
</style>
