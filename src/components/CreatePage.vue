<template>
  <div class="container mb-3">
    <form action="">
      <div class="mb-3">
        <div class="form-label">Page Title</div>
        <input type="text" name="" id="" class="form-control" v-model="pageTitle">
      </div>
      <div class="mb-3">
        <label for="" class="form-label">Content</label>
        <textarea type="text" class="form-control" name="" id="" cols="30" rows="10" v-model="pageContent"></textarea>
      </div>
      <div class="col">
        <div class="mb-3">
          <label for="" class="form-label">Link Text</label>
          <input type="text" name="" id="" class="form-control" v-model="linkName">
        </div>
        <div class="mb-3">
          <label for="" class="form-label">Link URL</label>
          <input type="text" name="" id="" class="form-control" v-model="linkURL">
        </div>
        <div class="mb-3">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" name="" id="" v-model="published">
            <label for="" class="form-check-label">Published</label>
          </div>
        </div>
      </div>
      <div class="mb-3">
        <button class="btn btn-primary" :disabled="isFormInvalid" @click.prevent="submitForm()">Create Page
        </button>
      </div>
    </form>
  </div>
</template>

<script>
	export default {
    // pageCreated are props that's a callback function defined by App.vue later
		// props: ['pageCreated'],
    emits: {
      pageCreated(link, title, content) {
        if (!link || !title || !content) return false
        return true
      }
    },
    computed: {
      isFormInvalid() {
        return !this.pageTitle || !this.pageContent || !this.linkName || !this.linkURL
      }
    },
		data() {
			return {
				pageTitle: '',
				pageContent: '',
				linkName: '',
				linkURL: '',
        published: true
			}
		},
    methods: {
      submitForm() {
        if (!this.pageTitle || !this.pageContent || !this.linkName || !this.linkURL) {
          alert('Please fill the form')
          return
        }

        this.$emit('pageCreated', {
          link: {name: this.linkName, url: this.linkURL},
          title: this.pageTitle,
          content: this.pageContent,
          published: this.published
        })

        this.clearFields()
      },

      clearFields() {
        this.pageTitle = ''
				this.pageContent = ''
				this.linkName = ''
				this.linkURL = ''
        this.published = true
      }
    },
    watch: {
      pageTitle(newTitle, oldTitle) {
        if (this.linkName === oldTitle) this.linkName = newTitle
      }
    }
	}
</script>

<style scoped></style>
