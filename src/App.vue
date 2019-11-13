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
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="prefix in prefixes"
                    v-bind:key="prefix"
                  >
                    {{ prefix }}
                  </li>
                </ul>
                <br />
                <input
                  class="form-control"
                  type="text"
                  placeholder="Digite o prefixo"
                />
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
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sufix in sufixes"
                    v-bind:key="sufix"
                  >
                    {{ sufix }}
                  </li>
                </ul>
                <br />
                <input
                  class="form-control"
                  type="text"
                  placeholder="Digite o sufixo"
                />
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
                v-for="domain in domains"
                v-bind:key="domain"
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
      prefixes: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: [
        'AirHub',
        'AirStation',
        'AirMart',
        'JetHub',
        'JetStation',
        'JetMart',
        'FlightHub',
        'FlightStation',
        'FlightMart'
      ]
    };
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
