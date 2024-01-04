<template>
  <div class="backdrop" @click="closeModal">
    <!-- <div class="backdrop" @click.self="closeModal"> -->
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- <h1>{{ header }}</h1>
      <p>{{ newName }}</p> -->
      <slot>default content</slot>
      <!-- slot dung de thay the code tu cha truyen vao -->
      <div class="actions">
        <slot name="myLinks"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["header", "newName", "theme"],
  // data() {
  //   return {
  //     title: "default title",
  //   };
  // },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}
.modal p {
  font-style: normal;
}
.modal.sale {
  background: purple;
}
.modal.sale h1 {
  color: white;
}
.modal.actions {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
.modal.sale .actions a {
  color: white;
}
.modal.sale .actions {
  color: white;
}
</style>
