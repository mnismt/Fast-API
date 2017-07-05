<template>
    <div id="app" class="columns">
        <div class="column is-half is-offset-one-quarter">
            <form @submit.prevent="sendRequest()">
                <div class="field">
                    <label class="label">URL</label>
                    <p class="control">
                        <input class="input" type="text" placeholder="URL input" v-model="url">
                    </p>
                </div>
                <div class="field">
                    <p class="control">
                        <label class="radio">
                        <input type="radio" name="question" value="get" v-model="method">
                        GET
                        </label>
                        <label class="radio">
                        <input type="radio" name="question" value="post" v-model="method">
                        POST
                        </label>
                    </p>
                </div>
                <button class="button is-primary" type="submit">GO</button>
            </form>
            <pre class="language-javascript">
            {{data}}
            </pre>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data () {
    return {
        url: '',
        method: 'get',
        data: ''
    }
  },
  methods: {
      sendRequest () {
          axios({
            method: this.method,
            url: this.url,
        }).then((response) => {
            this.data = response.data;
        }).catch((response) => {
            this.data = response;
        });
      }
  }
}
</script>
