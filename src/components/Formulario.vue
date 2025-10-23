<script setup>
import { reactive } from "vue";
import Alerta from "./Alerta.vue";

const alerta = reactive({
  tipo: "",
  mensaje: "",
});

defineEmits(['update:nombre','update:propietario','update:email','update:alta','update:sintomas'])

const props = defineProps({
    nombre: {
        type: String,
        required: true
    }
})

const validar = () => {
  if (Object.values(paciente).includes("")) {
    (alerta.mensaje = "Todos los campos son obligatorios"), (alerta.tipo = "error");
    return;
  }

  console.log("agregando");
};
</script>
<template>
  <div class="md:w-1/2">
    <h2 class="text-3xl font-black text-center">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade Pacientes y <span class="text-indigo-600 font-bold">Adminístralos</span>
    </p>

    <Alerta v-if="alerta.mensaje" :alerta="alerta" />

    <form
      @:submit.prevent="validar"
      action=""
      method="get"
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
    >
    {{ nombre }}
      <!-- MANERA 1 CON UN INLINEHADLER -->
      <div class="mb-5">
        <label for="mascota" class="block text-gray-700 uppercase font-bold"
          >Nombre de Mascota</label
        >
        <input
          id="mascota"
          type="text"
          placeholder="Nombre de la Mascota"
          class="w-full border-2 mt-2 p-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:nombre', $event.target.value)"
        />
      </div>

      <!-- MANERA 2 CON METOD HADLER -->
      <div class="mb-5">
        <label for="propietario" class="block text-gray-700 uppercase font-bold"
          >Nombre del propietario</label
        >
        <input
          id="propietario"
          type="text"
          placeholder="Nombre del propietario"
          class="w-full border-2 mt-2 p-2 placeholder-gray-400 rounded-md"
          
        />
      </div>

      <div class="mb-5">
        <label for="email" class="block text-gray-700 uppercase font-bold">Email</label>
        <input
          id="email"
          type="email"
          placeholder="Introduce tu email"
          class="w-full border-2 mt-2 p-2 placeholder-gray-400 rounded-md"
          
        />
      </div>

      <div class="mb-5">
        <label for="alta" class="block text-gray-700 uppercase font-bold">Alta</label>
        <input
          id="alta"
          type="date"
          class="w-full border-2 mt-2 p-2 placeholder-gray-400 rounded-md"
          
        />
      </div>

      <div class="mb-5">
        <label for="sintomas" class="block text-gray-700 uppercase font-bold"
          >Síntomas</label
        >
        <textarea
          id="sintomas"
          placeholder="Describe los sintomas de tu paciente"
          class="w-full border-2 mt-2 p-2 placeholder-gray-400 rounded-md h-20"
          
        />
      </div>

      <input
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors"
        type="submit"
        value="Registrar Paciente"
      />
    </form>
  </div>
</template>
