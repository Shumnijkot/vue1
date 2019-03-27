<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Name:</label>
            <input v-model="nameText" type='text'>
          </div>
          <div class='field'>
            <label>Desctiption:</label>
            <input v-model="descriptionText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nameText: '',
      descriptionText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.nameText.length > 0 && this.descriptionText.length > 0) {
        const searchParams = new URLSearchParams();

        searchParams.set("name", this.nameText);


        const body = searchParams;
        fetch("http://localhost:8080/api/products",{
          method:"POST",
          headers:{"content-type":"application/x-www-form-urlencoded"},
          body
        }).then(()=>{
          this.$emit('create-product', {
            name: this.nameText,
            description: this.descriptionText
          })
        });
        this.nameText = '';
        this.descriptionText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>
