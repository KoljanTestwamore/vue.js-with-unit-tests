<template>
  <div
    class="menu"
  >
    <div
      v-if="tray.length > 1"
      class="menu__back-item"
      @click="handleBack"
    >
      ↩️ Назад
    </div>
    <Item
      v-for="item in tray[tray.length - 1]"
      :key="item.id"
      :info="item"
      @clicked="addSubmenu"
    />
  </div>
</template>

<script>
import Item from './Item.vue';

export default {
  components: {
    Item,
  },
  props: {
    menu: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      menuItems: [],
      tray: [this.menu],
    };
  },
  methods: {
    addSubmenu(submenu) {
      this.tray.push(submenu);
    },
    handleBack() {
      this.tray.pop();
    },
  },
};
</script>

<style lang="scss" scoped>
.menu {
  width: 100%;
  position: absolute;
  border: 1px solid #000;
  z-index: 1;

  &__back-item {
    padding: 10px;
    background-color: rgb(228, 228, 228);
  }
}

</style>
