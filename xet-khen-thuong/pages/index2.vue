<template>
  <v-form @submit.prevent="onSubmit">
    <v-layout>
      <v-flex class="align-items-baseline">
        <div class="input">
          <v-file-input
            multiple
            label="File điểm học tập"
            @change="onPick"
          ></v-file-input>
        </div>
        <v-btn class="ma-2" outlined color="indigo" type="submit"
          >Bước tiếp theo</v-btn
        >
        <div></div>
        {{ dataSheets }}
      </v-flex>
    </v-layout>
  </v-form>
</template>
<script>
import XLSX from 'xlsx'
export default {
  data() {
    return {
      dataSheets: {},
      file: undefined,
    }
  },
  methods: {
    _file(file) {
      const reader = new FileReader()
      reader.onload = (e) => {
        const bstr = e.target.result
        const wb = XLSX.read(bstr, { type: 'binary' })
        // Get all worksheets
        const sheets = wb.SheetNames
        const result = {}
        sheets.forEach(function (sheetName) {
          const roa = XLSX.utils.sheet_to_json(wb.Sheets[sheetName], {
            header: 1,
          })
          if (roa.length) result[sheetName] = roa
        })
        JSON.stringify(result, 2, 2)
        // eslint-disable-next-line no-unreachable
        this.dataSheets = result
      }
      reader.readAsBinaryString(file)
    },
    onSubmit(evt) {
      if (this.file) this._file(this.file[0])
    },
    onPick(file) {
      this.file = file
      console.log(file)
    },
  },
}
</script>
