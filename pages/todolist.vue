<template>
  <div class="mt-5">
    <b-form @submit.prevent="onSubmit">
      <b-form-group id="input-group-2" label="To Do List:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.todo"
          required
          placeholder="Enter To Do List"
        />
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <div id="app" class="mt-5">
      <b-table :items="items" striped hover :fields="fields">
        <template v-slot:cell(action)="row">
          <div>
            <!--            <h5>{{ row.item.name }}</h5>-->
            <b-button
              size="sm"
              variant="danger"
              @click="deleteData(row.item.id)"
              ><b-icon-trash
            /></b-button>
          </div>
        </template>
      </b-table>
    </div>
  </div>
</template>

<script>
import { BIconTrash } from 'bootstrap-vue'

export default {
  components: {
    BIconTrash
  },
  async asyncData({ $axios }) {
    const items = await $axios.$get('list-data')
    return { items: items.list }
  },
  data() {
    return {
      form: {
        todo: ''
      },
      show: true,
      fields: [
        {
          key: 'id',
          label: 'Id'
        },
        {
          key: 'todo',
          label: 'Name'
        },
        {
          key: 'action',
          label: 'action'
        }
      ]
      // items: [
      //   {
      //     id: 0,
      //     name: 'Test 0'
      //   },
      //   {
      //     id: 1,
      //     name: 'Test 1'
      //   },
      //   {
      //     id: 2,
      //     name: 'Test 2'
      //   }
      // ]
    }
  },
  methods: {
    deleteData(id) {
      this.$axios.$delete('delete/' + id).then((response) => {
        this.items = this.items.filter((item) => {
          return item.id !== id
        })
      })
    },
    onSubmit() {
      this.$axios
        .$post('create', {
          todo: this.form.todo
        })
        .then((response) => {
          this.items.push({
            // id: Math.ceil(Math.random() * 10),
            id: response.data.id,
            todo: response.data.todo
          })
          this.$nextTick(() => {
            this.form.todo = ''
          })
        })
      // alert(JSON.stringify(this.form))
    },
    onReset(evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.todo = ''
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>
