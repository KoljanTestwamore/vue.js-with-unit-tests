<template>
  <div
    class="menu__item"
    @click="submenuClicked"
  >
    <a
      v-if="!info.submenu"
      class="menu__link"
      :href="`https://gdematerial.ru/catalog/${info.slug}-${info.id}`"
    >
      <span>
        {{ info.name }}
      </span>
      <span>
        ➡️
      </span>
    </a>
    <div
      v-else
    >
      {{ info.name }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      required: true,
    },
  },
  methods: {
    submenuClicked() {
      this.$emit('clicked', this.info.submenu);
    },
  },
};
</script>

<style lang="scss" scoped>
.menu {
  &__item {
    width: 100%;
    color: #000;
    padding: 10px;
    background-color: #fff;
  }

  &__link {
    display: flex;
    justify-content: space-between;
    color: #000;
    &:visited {
      color:#000;
    }
  }
}
</style>
