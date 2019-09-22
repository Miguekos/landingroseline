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
                id="correo"
                type="text"
                v-model.trim="form.correo"
                label="Correo"
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
                label="Telefono"
                required
                autofocus
              />
              <q-input
                id="precio"
                color="white"
                bg-color="red-3"
                filled
                type="text"
                v-model.trim="form.precio"
                label="Precio"
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
import { mapActions } from "vuex";
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
    ...mapActions("auth", ["login", "validarUser"]),
    async onSubmit() {
      this.loading1 = true;
      // this.getCliente();
      const data = {
        email: this.form.username,
        password: this.form.password
      };
      // console.log(data);
      const response = await this.login(data);
      const validar = response[0];
      console.log(validar);
      if (validar) {
        console.log("entro en validar");
        this.$q.notify({
          message: `Wellcome: ${validar.name}`,
          color: "green"
        });
        console.log(validar);
        localStorage.setItem("jwt", true);
        localStorage.setItem("datadelusuario", JSON.stringify(validar));
        this.$q.cookies.set("accToken", "cookie_value");
        this.$router.push("/");
        // this.$router.push({ name: "HelloWorld" });
      } else {
        this.$q.notify({
          message: "validar",
          color: "red"
        });
      }
      this.loading1 = false;
      // this.login()
    }
  },
  async mounted() {}
};
</script>
