<template>
  <v-form>
    <v-layout>
      <v-flex class="align-items-baseline">
        <div class="input">
          <v-text-field label="Nhập năm đánh giá danh hiệu"></v-text-field>
          <v-file-input multiple label="File điểm học tập"></v-file-input>
          <v-file-input multiple label="File điểm rèn luyện"></v-file-input>
          <v-file-input multiple label="File chức vụ"></v-file-input>
        </div>
        <v-btn class="ma-2" outlined color="indigo">Bước tiếp theo</v-btn>
      </v-flex>
    </v-layout>
    <v-bottom-navigation :value="activeBtn" grow color="teal" absolute>
      <v-btn>
        <span class="indigo--text lighten-2">Tải file excel</span>
        <span class="indigo--text lighten-2">Bước 1</span>
        <v-icon>mdi-briefcase-upload</v-icon>
      </v-btn>

      <v-btn>
        <span class="indigo--text lighten-2">Kiểm tra dữ liệu</span>
        <span class="indigo--text lighten-2">Bước 2</span>
        <v-icon>mdi-information</v-icon>
      </v-btn>

      <v-btn>
        <span class="indigo--text lighten-2">Hoàn thành</span>
        <span class="indigo--text lighten-2">Bước 3</span>
        <v-icon>mdi-briefcase-check</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </v-form>
</template>
<script>
export default {
  data() {
    return {
      activeBtn: 0,
    }
  },
}
</script>
