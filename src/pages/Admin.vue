<template>
  <div>
    <div class="q-pa-sm">
      <q-card class="q-pa-sm shadow-2 rounded-borders">
        <!--          <div class="text-h6 text-center">Iniciar Session</div>-->
        <div class="q-pa-sm flex-center flex">
          <div>
            <!-- <q-img src="/statics/01.png" style="width: 180px"></q-img> -->
            <img
              class="float-left"
              spinner-color="white"
              sizes="30px"
              src="/statics/LogoBlanco.png"
            />
          </div>
        </div>

        <div class="q-pa-md">
          <q-table
            title="leads"
            dense
            :data="data"
            :columns="columns"
            row-key="name"
          />
        </div>
      </q-card>
    </div>
  </div>
</template>

<script>
// import { mapActions } from "vuex";
export default {
  data() {
    return {
      loading1: false,
      drawerState: false,
      rememberMe: true,
      form: {
        username: "",
        correo: "",
        telf: "",
        precio: ""
      },
      columns: [
        {
          name: "name",
          required: true,
          label: "Nombre",
          align: "left",
          field: row => row.name,
          format: val => `${val}`,
          sortable: true
        },
        {
          name: "celular",
          align: "center",
          label: "Celular",
          field: "celular",
          sortable: true
        },
        { name: "correo", label: "Correo", field: "correo", sortable: true },
        { name: "servicio", label: "Servicio", field: "servicio" },
        { name: "paquetes", label: "Paquetes", field: "paquetes" },
        { name: "comentarios", label: "Comentarios", field: "comentarios" }
      ],
      data: []
    };
  },
  methods: {
    // ...mapActions("auth", ["login", "validarUser"]),
    async onSubmit() {}
  },
  async mounted() {
    this.$axios
      .get(`http://144.217.14.34:3000/api/prospectos`)
      .then(resp => {
        // console.log(resp.data);
        this.data = resp.data;
        this.$q.notify({
          message: "Prospectos Cargados",
          color: "blue",
          position: "top-right"
        });
      })
      .catch(() => {
        this.$q.notify({
          message: "Error al cargar",
          color: "red",
          position: "top-right"
        });
      });
  }
};
</script>
