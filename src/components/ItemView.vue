<template>
  <div>
    <b-card
      title="Card Title"
      tag="article"
      style="max-width: 20rem"
      class="mb-2 item-view"
    >
      <img :src="item.image" alt="" />

      <b-card-text>
        {{ item.name }}
      </b-card-text>

      <b-button @click="addToCard(item)" variant="primary"
        >Sepete Ekle</b-button
      >
    </b-card>
  </div>
</template>
<script>
import Item from "../store/Items";
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  methods: {
    addToCard(item) {
      console.log(item);
      this.$root.$emit("denemFunc", "deneme value")
      Item.cartItems.push(item);
    },
  },
};
</script>
<style>
.item-view {
  margin: 25px;
}
</style>
