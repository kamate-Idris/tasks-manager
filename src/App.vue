<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Tasks Manager" :showAddTask="showAddTask" />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>


<script >
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

export default {
  name: "App",
  components: {
    Header,
    Footer
  },
  data() {
    return { showAddTask: false }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },

  }
}

</script>

<style scoped>
.container {
  border: 1px solid blue;
  width: 700px;
  padding: 40px;
  position: absolute;
  top: 100px;
}
</style>
