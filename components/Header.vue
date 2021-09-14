<template>
  <header class="header">
    <div class="container">
      <nav class="header__nav">
        <div class="header__nav_logo">
          <a href="#">Test Logo</a>
        </div>
        <ul class="header__nav_list">
          <li class="header__nav_list_item">
            <a href="#">Курсы</a>
          </li>
          <li class="header__nav_list_item">
            <a href="#">Для детей</a>
          </li>
          <li class="header__nav_list_item">
            <a href="#"> Для взрослых</a>
          </li>
          <li class="header__nav_list_item">
            <a href="#"> По уровню немецкого</a>
          </li>

          <li class="header__nav_list_item">
            <a href="#"> О проекте</a>
          </li>
          <li class="header__nav_list_item">
            <a href="#">Определить уровень онлайн</a>
          </li>
          <li class="header__nav_list_item">
            <a href="#"> Контакты</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style lang="scss" scoped>
.header {
  background-color: #5d60a8;
  padding: 29px 0 24px 0px;
  &__nav {
    display: flex;
    justify-content: space-between;
    &_logo {
      font-weight: bold;
      font-size: 36px;
      line-height: 49px;
      width: 30%;
      a {
        color: #fff;
        text-decoration: none;
      }
    }
    &_list {
      padding: 0;
      list-style: none;
      display: flex;
      justify-content: space-between;
      width: 70%;
      li {
        font-size: 14px;
        line-height: 19px;
        font-weight: bold;
        a {
          color: #fff;
          text-decoration: none;
        }
      }
    }
  }
}
</style>
