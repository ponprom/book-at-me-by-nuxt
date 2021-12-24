<template>
  <div>
    <a-modal :visible="visible" :title="title" @cancel="handleCancel">
      <div class="text-center">
        <a-form
          :form="form"
          :label-col="{ span: 6 }"
          :wrapper-col="{ span: 18 }"
          :label-align="'left'"
        >
          <a-form-item label="Image">
            <a-input v-model="form.img" placeholder="url" />
          </a-form-item>
          <a-form-item label="Book Name">
            <a-input v-model="form.bookNameTh" placeholder="Book Name" />
          </a-form-item>
          <a-form-item label="Authors">
            <a-input v-model="form.authors" placeholder="Authors" />
          </a-form-item>
          <a-form-item label="Type">
            <a-select v-model="form.type" placeholder="Type">
              <a-select-option
                v-for="option in options"
                :key="option.id"
                :value="option.id"
              >
                {{ option.name }}
              </a-select-option>
            </a-select>
          </a-form-item>
          <a-form-item label="Description">
            <a-textarea
              v-model="form.desc"
              placeholder="Description"
              :auto-size="{ minRows: 3, maxRows: 5 }"
            />
          </a-form-item>
        </a-form>
      </div>
      <template slot="footer">
        <a-button type="primary" class="bg-blue-500" @click="handleSubmit">
          Submit
        </a-button>
        <a-button @click="handleCancel"> Cancel </a-button>
      </template>
    </a-modal>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      default: null
    },
    visible: {
      type: Boolean,
      default: false
    },
    isEdit: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      form: {}
    }
  },
  computed: {
    title() {
      return this.isEdit ? 'Edit' : 'Create'
    },
    options() {
      return [
        { id: 1, name: 'Novel' },
        { id: 2, name: 'Comic' }
      ]
    }
  },
  watch: {
    visible(v) {
      if (!v) return
      if (this.item) {
        this.form = Object.assign(this.item)
      }
    }
  },
  methods: {
    handleCancel() {
      this.form = Object.assign({})
      this.$emit('cancel')
    },
    handleSubmit() {
      if (!this.isEdit) {
        this.form = Object.assign(this.form, {
          key: new Date().getTime()
        })
      }
      this.$emit('submit', this.form)
    }
  }
}
</script>

<style></style>
