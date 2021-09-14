<template>
  <div class="card">
    <div class="card-image">
      <img src="/image123.png" />
    </div>
    <div class="card-text">
      <p class="card-title">{{ model.name }}</p>
      <p class="card-offer">-10%</p>
      <div class="card-prices">
        <p class="fake-price">7299</p>
        <p class="real-price">34 999 грн</p>
      </div>
    </div>
    <div class="card-buttons">
      <button type="button">Подробнее</button>
      <button type="button" class="buy"><img src="/shop.png" /></button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    model: {
      type: Object
    }
  }
};
</script>

<style lang="scss" scoped>
.card {
  padding: 18px;
  box-shadow: 0px 1px 4px rgba(15, 26, 58, 0.22);
  border-radius: 10px;
  transition: all 0.2s ease-in-out;
  margin: 8px;
  min-width: 210px;
  .card-buttons {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 14px;
    opacity: 0;
    visibility: hidden;
    transition: all 0.2s ease-in-out;
    button {
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 8px;
      border: 1px solid #ec564f;
      color: #ec564f;
      font-weight: bold;
      font-size: 10px;
      line-height: 15px;
      width: 100%;
      background-color: transparent;
      cursor: pointer;
      width: 45%;
      height: 30px;
    }
    .buy {
      background-color: #ec564f;
    }
  }
  .card-image {
    text-align: center;
  }
  .card-text {
    margin-top: 30px;
    .card-title {
      font-size: 12px;
      line-height: 19px;
      color: #1c2338;
      margin-bottom: 4px;
      font-weight: bold;
    }
    .card-offer {
      font-weight: bold;
      font-size: 11px;
      line-height: 17px;
      width: 32px;
      height: 18px;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #ec564f;
      border-radius: 4px;
      color: #ffffff;
    }
    .card-prices {
      display: flex;
      align-items: center;
      margin-top: 10px;
      .fake-price {
        font-size: 12px;
        line-height: 19px;
        text-decoration: line-through;
        color: #757575;
      }
      .real-price {
        font-weight: bold;
        font-size: 18px;
        line-height: 28px;
        color: #000000;
        margin-left: 7px;
      }
    }
  }
  &:hover {
    box-shadow: 0px 1px 4px rgba(236, 86, 79, 0.26);
    .card-buttons {
      visibility: visible;
      opacity: 1;
    }
  }
}
</style>
