<template>
  <div class="filter">
    <h5>Тип просессоры</h5>
    <div class="filter__input">
      <input type="text" v-model="search" placeholder="Искать просессор" />
    </div>
    <div class="filter__list" v-if="!!filters.length">
      <div
        class="filter__list_item"
        v-for="filter in currentFilters"
        :key="`filter-${filter.id}`"
      >
        <label class="container-label">
          <input
            type="checkbox"
            :id="`checkmark-${filter.id}`"
            @click="toggleData($event, filter)"
          />
          <span class="checkmark"></span>
        </label>
        <label :for="`checkmark-${filter.id}`">{{ filter.name }}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    filters: {
      type: Array,
      default: []
    }
  },
  data() {
    return {
      search: ""
    };
  },
  methods: {
    toggleData({ target }, data) {
      if (target.checked) {
        this.$emit("onSelect", data);
      } else {
        this.$emit("unSelect", data);
      }
    }
  },
  computed: {
    currentFilters() {
      if (!!this.filters.length && this.search) {
        return this.filters.filter(el => {
          if (el.name.includes(this.search)) {
            return el;
          }
        });
      } else {
        return this.filters;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
h5 {
  font-weight: bold;
  font-size: 14px;
  line-height: 207%;
  color: #313131;
  margin-bottom: 11px;
  margin-top: 0;
}
.filter {
  max-width: 206px;
  width: 100%;
  &__input {
    max-width: 184px;
    margin-bottom: 11px;
    input {
      height: 32px;
      padding-left: 16px;
      border-radius: 3px;
      border: 1px solid rgba(49, 49, 49, 0.5);
      &:focus {
        outline: none;
      }
    }
  }
  &__list {
    overflow-y: scroll;
    overflow-x: hidden;
    max-height: 254px;
    &::-webkit-scrollbar {
      width: 2px;
    }

    /* Track */
    &::-webkit-scrollbar-track {
      background: #c4c4c4;
    }

    /* Handle */
    &::-webkit-scrollbar-thumb {
      background: #313131;
      border-radius: 3px;
    }

    /* Handle on hover */
    &::-webkit-scrollbar-thumb:hover {
      background: #555;
    }
    &_item {
      display: flex;
      align-items: center;
      label {
        input {
          margin: 0;
        }
      }
      label {
        margin-left: 13px;
        margin-bottom: 0;
        font-size: 14px;
        line-height: 29px;
        color: #989898;
      }
    }
  }
  .container-label {
    display: block;
    position: relative;
    padding-left: 35px;
    margin-bottom: 20px;
    cursor: pointer;
    font-size: 22px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    input {
      position: absolute;
      opacity: 0;
      cursor: pointer;
      height: 0;
      width: 0;
    }
    .checkmark {
      position: absolute;
      top: 0;
      left: 0;
      height: 14px;
      width: 14px;
      background-color: #eee;
      border: 2px solid rgba(49, 49, 49, 0.5);
      border-radius: 2px;
    }
  }
  /* On mouse-over, add a grey background color */
  .container-label:hover input ~ .checkmark {
    background-color: #ccc;
  }

  /* When the checkbox is checked, add a blue background */
  .container-label input:checked ~ .checkmark {
    background-color: #ec564f;
    border-color: #ec564f;
  }

  /* Create the checkmark/indicator (hidden when not checked) */
  .checkmark:after {
    content: "";
    position: absolute;
    display: none;
  }

  /* Show the checkmark when checked */
  .container-label input:checked ~ .checkmark:after {
    display: block;
  }
  .container-label .checkmark:after {
    left: 3px;
    top: 0px;
    width: 5px;
    height: 10px;
    border: solid white;
    border-width: 0 3px 3px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
  }
}
</style>
