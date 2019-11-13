<template>
  <div>
    <header class="header">
      <div class="text-center">
        <h1>NameGator</h1>
        <h6 class="text-secondary">
          Gerador de nomes utilizando Vue.js, GraphQL e NodeJS.
        </h6>
      </div>
    </header>
    <main class="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos
              <span class="badge badge-info">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <div class="input-group">
                  <input
                    class="form-control"
                    type="text"
                    v-model="prefix"
                    v-on:keyup.enter="addPrefix(prefix)"
                    placeholder="Digite o prefixo"
                  />
                  <div class="input-group-append">
                    <button class="btn btn-info" v-on:click="addPrefix(prefix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
                <br />
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="(prefix, index) in prefixes"
                    v-bind:key="index"
                  >
                    <div class="row">
                      <div class="col">{{ prefix }}</div>
                      <div class="col text-right">
                        <button
                          class="btn btn-danger"
                          v-on:click="deletePrefix(prefix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos
              <span class="badge badge-info">{{ sufixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <div class="input-group">
                  <input
                    class="form-control"
                    type="text"
                    v-model="sufix"
                    v-on:keyup.enter="addSufix(sufix)"
                    placeholder="Digite o sufixo"
                  />
                  <div class="input-group-append">
                    <button class="btn btn-info" v-on:click="addSufix(sufix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
                <br />
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="(sufix, index) in sufixes"
                    v-bind:key="index"
                  >
                    <div class="row">
                      <div class="col">{{ sufix }}</div>
                      <div class="col text-right">
                        <button
                          class="btn btn-danger"
                          v-on:click="deleteSufix(sufix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <br />
        <h5>
          Domínios
          <span class="badge badge-info">{{ domains.length }}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li
                class="list-group-item"
                v-for="(domain, index) in domains"
                v-bind:key="index"
              >
                {{ domain }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      prefix: '',
      sufix: '',
      prefixes: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: []
    };
  },
  created() {
    this.generate();
  },
  methods: {
    addPrefix(prefix) {
      this.prefixes.push(prefix);
      this.prefix = '';
      this.generate();
    },
    addSufix(sufix) {
      this.sufixes.push(sufix);
      this.sufix = '';
      this.generate();
    },
    deletePrefix(prefix) {
      this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
      this.generate();
    },
    deleteSufix(sufix) {
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
      this.generate();
    },
    generate() {
      this.domains = [];
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          this.domains.push(prefix + sufix);
        }
      }
    }
  }
};
</script>

<style>
.header {
  padding: 30px 0;
}

.main {
  background-color: #f1f1f1;
  padding: 30px 0;
}
</style>
