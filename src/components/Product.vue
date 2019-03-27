<template>
    <div>
        <div>
            <div class='header'>
                {{ product.name }}
                </div>
            <div class='meta'>
                {{ product.description }}
            </div>
        </div>
    </div>
</template>

<script type="text/javascript">
  export default {
    props: ['product'],
    data() {
      return {
        show: true,
      };
    },
  };
</script>
