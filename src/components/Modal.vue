<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{sale: theme==='sale'}">
      <!-- <h1>{{ mtitle }}</h1>
      <p>{{ text }}</p> -->

      <slot>default content</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        props:[ 'mtitle', 'text', "theme" ],
        methods: {
            closeModal() {
                this.$emit('close')
            }
        },
    }
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
        color: rgb(36, 185, 135);
        border: none;
        padding: 0;
    }
    .modal.sale{
        background-color: rgb(240, 126, 126);
        color: white;
    }
    .modal.sale h1{
        color: white;
    }
    .modal .actions{
        text-align: center;
        margin: 30px 0 10px 0;
    }
    .modal .actions a{
        color: rgb(64, 64, 64);
        padding: 8px;
        border: 1px solid rgb(212, 212, 212);
        border-radius: 5px;
        text-decoration: none;
        margin: 10px;
    }
    .modal.sale .actions{
        color: white;
    }
    .modal.sale .actions a{
        color: white;
    }
</style>