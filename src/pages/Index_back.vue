<template>
  <div>
    <div class="q-pa-md fixed-center" style="width: 370px;">
      <q-card class="q-pa-md shadow-2 rounded-borders">
        <!--          <div class="text-h6 text-center">Iniciar Session</div>-->
        <div class="q-pa-md flex-center flex">
          <div>
            <!-- <q-img src="/statics/01.png" style="width: 180px"></q-img> -->
            <img
              class="float-left"
              spinner-color="white"
              sizes="30px"
              src="/statics/logoLogin.png"
            />
          </div>
        </div>
        <form @submit.prevent.stop="onSubmit" class="shadow-2 rounded-borders">
          <div class="q-pa-md">
            <div class="q-gutter-sm text-left">
              <q-input
                color="white"
                bg-color="red-3"
                filled
                id="username"
                type="text"
                v-model.trim="form.username"
                label="Nombres"
                required
                autofocus
              />
              <q-input
                color="white"
                bg-color="red-3"
                filled
                id="telf"
                type="text"
                v-model.trim="form.telf"
                label="Telular"
                required
                autofocus
              />
              <q-input
                color="white"
                bg-color="red-3"
                filled
                id="correo"
                type="email"
                v-model.trim="form.correo"
                label="Correo"
                required
                autofocus
              />
              <q-input
                id="paquetes"
                color="white"
                bg-color="red-3"
                filled
                type="text"
                v-model.trim="form.paquetes"
                label="Paquetes desde S/"
                required
                autofocus
              />
              <q-input
                id="Comen"
                color="white"
                bg-color="red-3"
                filled
                type="text"
                v-model.trim="form.servicio"
                label="Comentarios"
                required
                autofocus
              />
            </div>
          </div>
          <q-card-actions>
            <q-btn
              :loading="loading1"
              type="submit"
              class="fit"
              color="positive"
              >Suscribir</q-btn
            >
          </q-card-actions>
        </form>
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
      }
    };
  },
  methods: {
    // ...mapActions("auth", ["login", "validarUser"]),
    async onSubmit() {}
  },
  async mounted() {}
};
</script>
