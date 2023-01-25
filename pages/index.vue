<template>
  <div>
    <v-form>
      <v-file-input
        v-model="pdf"
        ref="pdfInput"
        label="Upload PDF"
        @change="uploadPdf"
      ></v-file-input>
    </v-form>
    <a v-if="pdfUrl" :href="pdfUrl" target="_blank">Open PDF</a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pdf: null,
      pdfUrl: "",
    };
  },
  methods: {
    uploadPdf() {
      if (!this.pdf) return;
      let reader = new FileReader();
      reader.readAsDataURL(this.pdf);
      reader.onload = (e) => {
        this.pdfUrl = e.target.result;
      };
    },
  },
};
</script>
