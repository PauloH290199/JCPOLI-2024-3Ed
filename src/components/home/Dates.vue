 
<template>
  <div style="margin:40px 0">
    <div>
      <span class="sub-title text-uppercase">Atenção com as datas</span>
    </div>
    <div style="max-width:700px;margin: 30px auto 10px;">
      <v-data-table
        hide-headers
        :items="dates"
        hide-actions
        class="elevation-1 datas"
        item-key="id"
        loading="true"
        no-data-text="Nenhum dado cadastrado"
      >
        <template v-slot:items="props">
          <tr>
            <td class="text-xs-center">
              <del v-if="props.item.disabled">{{ props.item.date }}</del>
              <span v-else>{{ props.item.date }}</span>
            </td>
            <td class="text-xs-center">
              <del v-if="props.item.disabled">{{ props.item.event }}</del>
              <span v-else>{{ props.item.event }}</span>
            </td>
          </tr>
        </template>
      </v-data-table>
    </div>
  </div>
</template>


<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'

@Component({
  components: {}
})
export default class Dates extends Vue {
  private headers = [
    {
      text: 'data',
      align: 'left',
      value: 'date',
      sortable: false
    },
    {
      text: 'data2',
      align: 'right',
      value: 'date',
      sortable: false
    }
  ]

  private dates = [
    {
      date: '10 a 23 de Abril de 2023',
      event: 'Período para encaminhamento dos artigos e resumos expandidos',
      disabled: false
    },
    {
      date: 'Até 01 de Maio de 2023',
      event: 'Período para avaliação, revisão e correção dos artigos e resumos expandidos',
      disabled: false
    },
    {
      date: '09 de Maio de 2023',
      event: 'Apresentação dos artigos e resumos expandidos na II JCPOLI',
      disabled: false
    }
  ]

  constructor() {
    super()
  }
}
</script>

<style scoped>
.sub-title {
  font-size: 20px;
  color: #0065a0;
  font-weight: 600;
  font-family: 'Montserrat', sans-serif;
}

.datas td {
  font-size: 16px;
}
</style>