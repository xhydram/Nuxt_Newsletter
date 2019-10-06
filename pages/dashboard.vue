<template>
  <div>
    <div class="w-75 mr-auto ml-auto mt-5">
      <b-button variant="dark" class>+ Add Newsletter</b-button>
      <table
        class="table table-striped table-bordered mt-3 table-styles"
        v-if="newsletters_data.length > 0"
      >
        <thead class="thead-dark">
          <tr>
            <th>Title</th>
            <th>Description</th>
            <th class="text-center">Image</th>
            <th class="text-center">Target</th>
            <th class="text-center">Subscribed</th>
            <th class="text-center">Edit</th>
            <th class="text-center">Remove</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="news in newsletters_data" :key="news.id">
            <td>{{ news.title }}</td>
            <td>{{ news.description }}</td>
            <td class="overflow-hidden ssss">{{ news.image }}</td>
            <td class="text-center">{{ news.target }}</td>
            <td class="text-center">{{ news.subscribed }}</td>
            <td class="text-center">
              <i class="edit fas fa-edit" @click.prevent="editar( news )" v-b-modal.modal-edit></i>
            </td>
            <td class="text-center">
              <i class="remove fas fa-trash-alt" @click.prevent="eliminar( news.id )"></i>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <b-modal id="modal-edit" ref="modal" :title="news_selected.title" @ok="handleOk">
      <form ref="form" @submit.stop.prevent="handleSubmit">
        <label for="title-input">Title:</label>
        <b-form-input
          id="name-input"
          required
          class="w-100"
          :value="news_selected.title"
          v-model="aux_news_edit.title"
        ></b-form-input>
        <label for="description-input">Description:</label>
        <b-form-input
          id="name-input"
          required
          class="w-100"
          :value="news_selected.description"
          v-model="aux_news_edit.description"
        ></b-form-input>
        <label for="target-input">Target:</label>
        <b-form-input
          id="name-input"
          required
          class="w-100"
          :value="news_selected.target"
          v-model="aux_news_edit.target"
        ></b-form-input>
        <label for="image-input">Image:</label>
        <b-form-input
          id="name-input"
          required
          class="w-100"
          :value="news_selected.image"
          v-model="aux_news_edit.image"
        ></b-form-input>
        <div class="fluid-container d-flex justify-content-center margin-top">
          <img :src="aux_news_edit.image" class="w-50" />
        </div>
      </form>
    </b-modal>
  </div>
</template>

<script>
import axios from "axios";
import BootstrapVue from "bootstrap-vue";
import Menu from "@@/components/Menu";

export default {
  layout: "dashboard",

  components: {
    Menu
  },

  created() {
    const url = "https://newsletters.academlo.com/api/v1/newsletters";

    axios.get(url).then(response => {
      this.newsletters_data = response.data;
    });
  },

  data: () => {
    return {
      newsletters_data: [],
      news_selected: {},
      aux_news_edit: {
        id: -1,
        title: "",
        description: "",
        target: -1,
        image: ""
      }
    };
  },

  methods: {
    editar(news) {
      this.news_selected = news;
      this.aux_news_edit.id = this.news_selected.id;
      this.aux_news_edit.title = this.news_selected.title;
      this.aux_news_edit.description = this.news_selected.description;
      this.aux_news_edit.target = this.news_selected.target;
      this.aux_news_edit.image = this.news_selected.image;
      console.log(this.news_selected);
    },

    eliminar(id) {
      this.newsletters_data = this.newsletters_data.filter(function(
        value,
        index,
        arr
      ) {
        return value.id != id;
      });
    },

    handleOk(bvModalEvt) {
      console.log(this.aux_news_edit);
      this.news_selected.title = this.aux_news_edit.title;
      this.news_selected.description = this.aux_news_edit.description;
      this.news_selected.target = this.aux_news_edit.target;
      this.news_selected.image = this.aux_news_edit.image;
    }
  }
};
</script>

<style scoped>
.table-styles {
  margin-top: 150px;
}

.color-orange {
  color: orange;
}

.color-red {
  color: red;
}

input {
  width: 100px;
}

.margin-top {
  margin-top: 20px;
}

.remove,
.edit {
  cursor: pointer;
}

.remove {
  color: red;
}

.edit {
  color: green;
}

.edit:hover {
  text-shadow: 1px 0.5px rgba(0, 128, 0, 0.465);
}

.remove:hover {
  text-shadow: 1px 0.5px rgba(199, 4, 4, 0.465);
}

.ssss {
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  font-size: 1rem;
}
</style>