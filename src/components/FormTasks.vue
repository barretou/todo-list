<template>
  <div>
    <h3>Formulario</h3>
    <b-form>
      <b-form-group label="Titulo" label-for="Subject">
        <b-form-input
          id="subject"
          v-model="form.subject"
          type="text"
          placeholder="Ex: lavar carro"
          required
          autocomplete="off"
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Descrição" label-for="Description">
        <b-form-textarea
          id="description"
          v-model="form.description"
          type="text"
          placeholder="Ex: abastecer o carro e lavar"
          required
          autocomplete="off"
        ></b-form-textarea>
      </b-form-group>

      <b-button type="submit" variant="primary" @click="saveTask"
        >Salvar</b-button
      >
    </b-form>
  </div>
</template>

<script>
import toastMixin from '@/mixins/toastMixin.js';
export default {
  name: "FormTasks",
  mixins: [toastMixin],
  data() {
    return {
      form: {
        subject: "",
        description: "",
      },
      methodSave: "new",
    };
  },
  created(){
    if(this.$route.params.index === 0 || this.$route.params.index !== undefined){
      this.methodSave = "update";
      let tasks = JSON.parse(localStorage.getItem("tasks"));
      this.form = tasks[this.$route.params.index];
    }
  },
  methods: {
    saveTask() {
      if(this.methodSave === "update"){
        let tasks = JSON.parse(localStorage.getItem("tasks"));
        tasks[this.$route.params.index] = this.form;
        localStorage.setItem("tasks", JSON.stringify(tasks));
        this.showToast("success", "Sucesso","Tarefa atualizada com sucesso!");
        this.$router.push({ name: list });
        return;
      }

      let tasks = localStorage.getItem("tasks")
        ? JSON.parse(localStorage.getItem("tasks"))
        : [];
      tasks.push(this.form);
      localStorage.setItem("tasks", JSON.stringify(tasks));
      this.showToast("success", "Sucesso!", "Tarefa criada com suceso");
      this.$router.push({ name: list });
    },
  },
};
</script>

<style scoped>
</style>