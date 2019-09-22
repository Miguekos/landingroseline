<template>
  <div>
    <template>
      <q-img :src="url">
        <div class="text-subtitle2 flex flex-center">
          <q-img :src="url2" spinner-color="white" style="width: 250px" />
        </div>
      </q-img>
    </template>
    <div>
      <q-card class="q-pa-md shadow-2 rounded-borders">
        <!--          <div class="text-h6 text-center">Iniciar Session</div>-->
        <form @submit.prevent.stop="onSubmit" class="shadow-2 rounded-borders">
          <div class="q-pa-md">
            <div class="q-gutter-sm text-left">
              <q-input
                dense
                filled
                color="grey"
                id="username"
                type="text"
                v-model.trim="form.username"
                label="Nombres"
                required
                autofocus
              />
              <q-input
                filled
                dense
                color="grey"
                id="telf"
                type="text"
                v-model.trim="form.telf"
                label="Telular"
                required
              />
              <q-input
                filled
                dense
                color="grey"
                id="correo"
                type="email"
                v-model.trim="form.correo"
                label="Correo"
                required
              />
              <q-input
                filled
                dense
                color="grey"
                id="servicio"
                type="text"
                v-model.trim="form.servicio"
                label="Servicios"
                required
              />
              <q-input
                id="paquetes"
                color="grey"
                filled
                dense
                type="text"
                v-model.trim="form.paquetes"
                label="Paquetes desde S/"
                required
              />
              <q-input
                id="comentarios"
                color="grey"
                filled
                dense
                type="text"
                v-model.trim="form.comentarios"
                label="Comentarios"
                required
              />
            </div>
          </div>
          <q-card-actions>
            <q-btn :loading="loading1" type="submit" class="fit"
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
      url: "../statics/fondo3.png",
      url2: "../statics/LogoBlanco.png",
      loading1: false,
      drawerState: false,
      rememberMe: true,
      form: {}
    };
  },
  methods: {
    // ...mapActions("auth", ["login", "validarUser"]),
    async onSubmit() {
      this.loading1 = true;
      this.loading1 = false;
      // console.log(this.form);
    }
  },
  async mounted() {}
};
</script>
<style>
.q-img__content > div {
  position: absolute;
  padding: 16px;
  color: #ffffff;
  background: rgba(45, 45, 45, 0);
  padding-top: 25px;
}
</style>
