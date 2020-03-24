<template>
  <div>
    <h5 class="text-center text-white">Taal & Spelling</h5>
    <div id="form">
      <q-input
        filled
        dark
        v-model="title"
        label="Titel"/>
      <q-input
        filled
        dark v-model="numberOfQuestions"
        label="Aantal vragen"
        type="number"
        min="1"/>
      <q-btn
        type="submit"
        :loading="submitting"
        label="Exporteren"
        class="q-mt-md"
        color="primary"
        @click="submit"
      >
        <template v-slot:loading>
          <q-spinner-facebook/>
        </template>
      </q-btn>
    </div>
  </div>
</template>

<script>
    import {required} from 'vuelidate/lib/validators';
    import axios from 'axios';
    import FileSaver from 'file-saver';

    export default {
        name: "SpellingRekenen",
        data() {
            return {
                submitting: false,
                title: '',
                numberOfQuestions: 1,
            }
        },
        methods: {
            submit: function () {
                this.$v.$touch();
                if (!this.$v.$invalid) {
                    let url = "";
                    const data = {title: this.title, numberOfQuestions: this.numberOfQuestions};
                    Object.keys(data).forEach(function (e) {
                        url += e + "=" + data[e] + "&";
                    });
                    url = url.trim("&");
                    console.log(process.env.API + '/api/generate/taalspelling?' + url);
                    window.open(process.env.API + '/api/generate/taalspelling?' + url, '_blank');
                } else {
                    this.$q.notify({
                        type: 'negative',
                        message: 'Één of meerdere velden zijn onjuist ingevuld.'
                    })
                }
            }
        },
        validations: {
            title: {required},
            numberOfQuestions: {required},
        }
    }
</script>

<style scoped>

</style>
