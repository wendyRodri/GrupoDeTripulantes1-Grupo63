<template>
  <div class="container">
    <h1>Incidentes</h1>
    <b-alert
      :show="dismissCountDown"
      dismissible
      :variant="mensaje.color"
      @dismissed="dismissCountDown = 0"
      @dismiss-count-down="countDownChanged"
    >
      {{ mensaje.texto }}
    </b-alert>
  
    <form @submit.prevent="modificarIncidente(modSgo)" v-if="modificar">
      <h3>Modificar incidente</h3>
      <input
        type="date"
        placeholder="Fecha"
        v-model="modSgo.fecha"
      />
      <input
        type="text"
        class="mx-2"
        placeholder="Sede"
        v-model="modSgo.sede"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Apellido"
        v-model="modSgo.apellido"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Nombre"
        v-model="modSgo.nombre"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Creador"
        v-model="modSgo.creador"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Proceso"
        v-model="modSgo.proceso"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Validacion"
        v-model="modSgo.validacion"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Descripción incidente"
        v-model="modSgo.descripcionIncidente"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Investigador lider"
        v-model="modSgo.investigadorLider"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Severidad"
        v-model="modSgo.severidad"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Tipo incidente"
        v-model="modSgo.tipoIncidente"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Tipo Trabajador"
        v-model="modSgo.tipoTrabajador"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Validacion investigacion"
        v-model="modSgo.validacionInvestigacion"
      />
      <input
        type="number"
        class="form-control my-2"
        placeholder="Dias incapacidad"
        v-model="modSgo.diasPerdidos"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Tipo vinculación"
        v-model="modSgo.tipoTrabajador"
      />
      <button class="btn-success my-2" type="submit">Modificar</button>
      <button class="my-2" type="submit" @click="modificar = false">
        Cancelar
      </button>
    </form>
    <form @submit.prevent="adicionarIncidente()" v-if="!modificar">
      <h3>Ingresar nuevo incidente</h3>
      <input
        type="date"
        placeholder="Fecha"
        v-model="sgo.fecha"
      />
      <input
        type="text"
        class="mx-2"
        placeholder="Sede"
        v-model="sgo.sede"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Nombre"
        v-model="sgo.nombre"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Apellido"
        v-model="sgo.apellido"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Creador"
        v-model="sgo.creador"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Proceso"
        v-model="sgo.proceso"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Validacion"
        v-model="sgo.validacion"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Descripción incidente"
        v-model="sgo.descripcionIncidente"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Investigador lider"
        v-model="sgo.investigadorLider"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Severidad"
        v-model="sgo.severidad"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Tipo incidente"
        v-model="sgo.tipoIncidente"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Tipo Trabajador"
        v-model="sgo.tipoTrabajador"
      />
      <input
        type="text"
        class="form-control my-2"
        placeholder="Validacion investigacion"
        v-model="sgo.validacionInvestigacion"
      />
      <input
        type="number"
        class="form-control my-2"
        placeholder="Dias incapacidad"
        v-model="sgo.diasPerdidos"
      />
      <button class="btn-success" type="submit">Adicionar</button>
    </form>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Apellido</th>
          <th scope="col">Nombre</th>
          <th scope="col">Sede</th>
          <th scope="col">Fecha</th>
          <th scope="col">Creador</th>
          <th scope="col">Proceso</th>
          <th scope="col">Validacion</th>
          <th scope="col">Descripción incidente</th>
          <th scope="col">Investigador lider</th>
          <th scope="col">Severidad</th>
          <th scope="col">Tipo incidente</th>
          <th scope="col">Tipo Trabajador</th>
          <th scope="col">Validacion investigacion</th>
          <th scope="col">Dias perdidos</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in vectorSGO" :key="index">
          <th scope="row">{{ item._id }}</th>
          <td>{{ item.apellido }}</td>
          <td>{{ item.nombre }}</td>
          <td>{{ item.sede }}</td>
          <td>{{ item.fecha }}</td>
          <td>{{ item.creador }}</td>
          <td>{{ item.proceso }}</td>
          <td>{{ item.validacion }}</td>
          <td>{{ item.descripcionIncidente }}</td>
          <td>{{ item.investigadorLider }}</td>
          <td>{{ item.severidad }}</td>
          <td>{{ item.tipoIncidente }}</td>
          <td>{{ item.tipoTrabajador }}</td>
          <td>{{ item.validacionInvestigacion }}</td>
          <td>{{ item.diasPerdidos }}</td>
          <td>
            <b-button class="btn-warning btn-sm mx-2" @click="activarModificar(item._id)"> Modificar
            </b-button>
            <b-button class="btn-danger btn-sm mx-2" @click="eliminarIncidente(item._id)">
            X
            </b-button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      vectorSGO: [],
      sgo: {
        nombre: "",
        apellido: "",
        sede: "",
        fecha: Date.now(),
        creador: "",
        proceso: "",
        validacion: "",
        descripcionIncidente: "",
        investigadorLider: "",
        severidad: "",
        tipoIncidente: "",
        tipoTrabajador: "",
        validacionInvestigacion: "",
        diasPerdidos: 0,
      },
      modSgo: {},
      mensaje: { color: "success", texto: "" },
      dismissSecs: 5,
      dismissCountDown: 0,
      modificar: false
    };
  },

  created() {
    this.listarIncidentes();
  },

  methods: {
  
    countDownChanged(dismissCountDown) { 
    this.dismissCountDown = dismissCountDown 
    }, 
    showAlert() { 
    this.dismissCountDown = this.dismissSecs 
    },
    listarIncidentes() {
      this.axios
        .get("/incidentes")
        .then((res) => {
          console.log(res.data);
          this.vectorSGO = res.data;
        })
        .catch((e) => {
          console.log("error " + e.response);
        });
    },

    adicionarIncidente(item) {
      this.axios
        .post("/nuevo-incidente", this.sgo)
        .then((res) => {
          this.sgo.push(res.data);
          this.sgo.nombre = "";
          this.sgo.apellido = "";
          this.sgo.sede = "";
          this.sgo.fecha = Date.now;
          this.sgo.creador = "";
          this.sgo.proceso = "";
          this.sgovalidacion = "";
          this.sgo.descripcionIncidente = "";
          this.sgo.investigadorLider = "";
          this.sgo.severidad = "";
          this.sgo.tipoIncidente = "";
          this.sgo.tipoTrabajador = "";
          this.sgo.validacionInvestigacion = "";
          this.sgo.diasPerdidos = 0;

          // Alerta de mensaje
          this.mensaje.texto = "Incidente adicionado!";
          this.mensaje.color = "success";
          this.showAlert();
        })
        .catch((e) => {
          console.log("error" + e);
        });
    },

    eliminarIncidente(id) {
      this.axios
        .delete("buscarIncidente/${id}")
        .then((res) => {
          let index = this.vectorSGO.findIndex((item) => item._id === res.data._id);
          this.vectorSGO.splice(index, 1);
          this.mensaje.texto = "Incidente Eliminado!";
          this.mensaje.color = "danger";
          this.showAlert();
        })
        .catch((e) => {
          console.log(e.response);
        });
    },

    activarModificar(id) {
      this.modificar = true;
      this.axios
        .get("/buscarIncidente/${id}")
        .then((res) => {
          this.modSgo = res.data;
        })
        .catch((e) => {
          console.log(e.response);
        });
    },

    modificarIncidente(item) {
      this.axios
        .put("/buscarIncidente/${item._id}", item)
        .then((res) => {
          const index = this.vectorSGO.findIndex(
            itemInc => itemInc._id === res.data._id
          );
          this.vectorSGO[index].nombre = res.data.nombre;
          this.vectorSGO[index].apellido = res.data.apellido;
          this.vectorSGO[index].sede = res.data.sede;
          this.vectorSGO[index].fecha = res.data.fecha;
          this.vectorSGO[index].creador = res.data.creador;
          this.vectorSGO[index].proceso = res.data.proceso;
          this.vectorSGO[index].validacion = res.data.validacion;
          this.vectorSGO[index].descripcionIncidente =
            res.data.descripcionIncidente;
          this.vectorSGO[index].investigadorLider = res.data.investigadorLider;
          this.vectorSGO[index].severidad = res.data.severidad;
          this.vectorSGO[index].tipoIncidente = res.data.tipoIncidente;
          this.vectorSGO[index].tipoTrabajador = res.data.tipoTrabajador;
          this.vectorSGO[index].validacionInvestigacion =
            res.data.validacionInvestigacion;
          this.vectorSGO[index].diasPerdidos = res.data.diasPerdidos;
          this.mensaje.texto = "Incidente actualizado";
          this.mensaje.color = "success";
          this.showAlert();
          this.modificar = false;
        })
        .catch((e) => {
          console.log(e);
        });
      this.modificar = true;
    },
  },
};
</script>
