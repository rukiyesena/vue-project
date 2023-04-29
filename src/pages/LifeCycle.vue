<template>
  <div>
    <b-row>
      {{ cartItems }}
    </b-row>
    <b-row>
      <b-col
        cols="3"
        v-for="item in Items"
        :key="item.value"
        :value="item.value"
        :text="item.label"
      >
        <item-view :item="item"></item-view>
      </b-col>
    </b-row>
  </div>
</template>
<script>
import Items from "../store/Items";
import ItemView from "../components/ItemView.vue";
export default {
  components: {
    ItemView,
  },
  data() {
    return {
      val: 0,
      Items: Items.items,
      cartItems: Items.cartItems,
    };
  },
  methods:{
    denemFunc(param){
        console.log(param)
        console.log("denemFunc")
    }
  },
  beforeCreate() {
    console.log("beforeCreate()");
  },
  created() {
    console.log(this.Items);
    console.log("created()");
  },
  beforeMount() {
    console.log("beforeMount()");
  },
  mounted() {
    console.log("mounted()");
    this.$root.$on("denemFunc", (param) => {
      this.denemFunc(param);
    });
  },
  computed: {
    cartItemsVal() {
      console.log("computed");
      return this.cartItems;
    },
  },
  watch() {
    console.log("watch()");
  },
  beforeUpdate() {
    console.log("beforeUpdate()");
  },
  updated() {
    console.log("updated()");
  },
  beforeDestroy() {
    this.$root.$off("denemFunc");
  },
  destroyed() {
    console.log("destroyed()");
  },
};
</script>
