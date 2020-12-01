<template>
  <div class="container">
    <div class="row">
      <div class="col-12 h2 text-muted">Список автомобилей</div>
      <div class="form-group col-10 offset-1 col-sm-8 offset-sm-2 mt-4">
        <div class="row">
          <input
            class="col-8 col-sm-6 offset-sm-2 form-control"
            type="search"
            placeholder="Поиск"
            v-model.lazy="value"
            minlength="2"
            required
          />
          <button
            class="btn btn-sm btn-success col-4 col-sm-2"
            @click="searchInList()"
          >
            Искать
          </button>
        </div>
        <div class="row mt-1" v-if="success">
          <ul class="list-group col-sm-8 offset-sm-2 flex-wrap">
            <li
              class="list-group-item col mx-auto text-success font-weight-bold"
              v-for="item of newList"
              :key="item"
              :data-item="item"
            >
              {{item}}
            </li>
          </ul>
        </div>
        <div class="row mt-2" v-if="!success">
          <div class="col-12 mb-1">
            <p class="col-6 text-warning d-inline">Совпадений не найдено</p>
            <button @click="addNewValue()" class="btn btn-sm btn-outline-success">
              Добавить в список
            </button>
          </div>
        </div>
        <div class="row mt-1">
          <ul
            class="list-group list-group-horizontal col-sm-8 offset-sm-2 flex-wrap"
            @click="deleteItem"
          >
            <li
              class="list-group-item col-6 btn btn-primary"
              style="border-left-width: 1px"
              v-for="item in list"
              :key="item"
              :data-name="item"
            >
              {{item}}
            </li>
          </ul>
        </div>
        <div class="row">
          <div class="col-8 offset-2 mt-4">
            <small class="text-danger alert alert-danger">Кликните по ячейке для удаления</small>
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
      list: [
        "Audi",
        "BMW",
        "Mercedes",
        "Toyota",
        "Ford",
        "Chevrolet",
        "Nissan",
        "Hyundai",
        "KIA",
        "Opel",
        "Mazda",
        "Volkswagen",
        "Volvo",
        "Skoda",
        "Renault",
        "Honda",
        "LADA",
        "UAZ",
      ],
      value: "",
      newList: [],
      success: 'ready',
    }
  },
  methods: {
    async searchInList() {
      this.newList = [];
      await this.list.forEach((item) => {
        if (item.toLowerCase() == this.value.toLowerCase()) {
          this.newList.push(item);
          this.succes = true;
        } 
      });
      if (this.newList.length === 0) {
        this.success = false;
      }
    },
    addNewValue() {
      this.list.push(this.value);
      this.success = "ready";
      this.value = "";
    },
    deleteItem(event){
      const dataName = event.target.dataset.name
      this.list = this.list.filter(item => item != dataName)
    }
  },
};
</script>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
