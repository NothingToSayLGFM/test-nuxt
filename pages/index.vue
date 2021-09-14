<template>
  <div>
    <Header />
    <section>
      <Slider />
    </section>
    <section class="container container-content">
      <h2 class="title">Тестовый блок чекбоксы</h2>
      <div class="content">
        <ProductFilter
          :filters="filters"
          @onSelect="onSelect"
          @unSelect="unSelect"
        />
        <div class="products-container">
          <h3>Компьютеры</h3>
          <div class="products" v-if="currentSelects.length">
            <Card
              v-for="model in currentSelects"
              :key="`model-${model.category_id}`"
              :model="model"
            />
          </div>
          <div class="nothing" v-else>
            <h2>Nothing Found</h2>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      models: [
        { name: "Intel Core i7", type: "1", category_id: 1 },
        { name: "Intel Core i9", type: "2", category_id: 2 },
        { name: "Intel Core i9", type: "2", category_id: 3 },
        { name: "Intel Core i5", type: "3", category_id: 4 },
        { name: "Intel Core i5", type: "3", category_id: 5 },
        { name: "Intel Celeron", type: "4", category_id: 6 }
      ],
      filters: [
        { name: "Intel Core i7", type: "1", id: 1 },
        { name: "Intel Core i9", type: "2", id: 2 },
        { name: "Intel Core i5", type: "3", id: 3 },
        { name: "Intel Celeron", type: "4", id: 4 }
      ],
      currentSelects: []
    };
  },
  methods: {
    onSelect(data) {
      let products = this.models.filter(el => el.type === data.type);
      if (products.length) {
        this.currentSelects = [...this.currentSelects, ...products];
      }
    },
    unSelect(data) {
      let unselectedProduct = this.currentSelects.find(
        el => el.type === data.type
      );
      if (unselectedProduct) {
        this.currentSelects = [
          ...this.currentSelects.filter(
            el => el.type !== unselectedProduct.type
          )
        ];
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.container-content {
  margin-top: 150px;
  margin-bottom: 150px;
}
.content {
  display: flex;

  .products-container {
    margin-left: 24px;
    h3 {
      margin-top: 0px;
      margin-bottom: 24px;
    }
  }
  .products {
    display: flex;
    flex-wrap: wrap;
  }
}
.title {
  font-weight: bold;
  font-size: 48px;
  line-height: 65px;
  margin-bottom: 11px;
  color: #0e1027;
}
</style>
