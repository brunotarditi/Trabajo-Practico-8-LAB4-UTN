<template>
  <div style="margin-top:80px">
    <div
      v-for="instrumento in instrumentos"
      :key="instrumento.id"
      style="margin-top:15px"
      class="d-flex justify-content-center"
    >
      <instrumento-item :instrumentoParam="instrumento"></instrumento-item>
    </div>
  </div>
</template>

<script>
import Instrumento from "@/components/Instrumento.vue";
import axios from "axios";
export default {
  name: "Productos",
  components: {
    "instrumento-item": Instrumento,
  },
  mounted() {
    this.getInstrumentos();
  },
  data() {
    return {
      instrumentos: [],
    };
  },
  methods: {
    getInstrumentos() {
      axios.get("http://localhost:8080/instrumento").then((res) => {
        console.log(res.data);
        this.instrumentos = res.data;
      }).catch((err) => {
          console.log(err)
      });
    },
  },
};
</script>
