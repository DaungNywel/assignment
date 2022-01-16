<template>
  <v-app>
    <v-main>
      <v-container>
        <v-card class="mx-auto" max-width="800">
          <v-card-text>
            <v-file-input
              v-model="filename"
              accept="text/csv,.xml"
              style="width: 500px"
              label="File input"
              outlined
              dense
              @change="uploadFile($event)"
            ></v-file-input>
            <v-btn depressed color="primary" @click="AddClick"> Add </v-btn>
          </v-card-text></v-card
        >
      </v-container>
    </v-main>
  </v-app>
</template>
<script>
export default {
  name: "App",

  data: () => ({
    filename: "",
    web_url: "https://localhost:44370/",
  }),
  methods: {
    uploadFile(e) {
      alert(e);
      if (!/\.(csv|xml)$/.test(e.name)) {
        alert("Unknown format!");
        this.filename = e.name;
        return false;
      } 
      var reader = new FileReader();
       reader.onload = (e) => {
        let data;
        if (typeof e.target.result === "object") {
          data = window.URL.createObjectURL(new Blob([e.target.result]));
        } else {
          data = e.target.result;
        }      
        alert(data)
      };
    },
    AddClick() {
     
    },
  },
};
</script>
