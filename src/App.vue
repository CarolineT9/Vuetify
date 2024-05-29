<template>
  <v-app>
    <!--Barra lateral-->
    <v-navigation-drawer v-model="drawer">
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>
        <v-list-item prepend-icon="mdi-home">Home</v-list-item>

        <v-list-group value="users">
          <template #activator="{ props }">
            <v-list-item v-bind="props" prepend-icon="mdi-account" title="Usuários">

            </v-list-item>
          </template>

          <v-list-item prepend-icon="mdi-currency-usd">Faturamento</v-list-item>
          <v-list-item prepend-icon="mdi-file-chart">Relatório</v-list-item>
        </v-list-group>

      </v-list>

    </v-navigation-drawer>

    <!--Barra superior-->
    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon @click='toggleDrawer'></v-app-bar-nav-icon>
      <v-app-bar-title>Meu app</v-app-bar-title>
      <template #append>
        <v-btn icon="" density="comfortable" class="mr-3">
          <v-badge dot>
            <v-icon icon="mdi-bell"></v-icon>
          </v-badge>
        </v-btn>

        <!--Menu dropdown-->
        <v-menu>
          <template #activator="{ props }">
            <v-avatar class="ma-3" v-bind="props">
              <v-img cover
                src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"></v-img>

            </v-avatar>
          </template>
          <v-card min-width="200">
            <v-container>
              <v-list :lines="false" density="compact" nav>
                <v-list-item prepend-icon="mdi-account-circle">
                  <v-list-item-title>Meu Perfil</v-list-item-title>
                </v-list-item>
                <v-list-item prepend-icon="mdi-heart">
                  <v-list-item-title>Meus favoritos</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-container>

          </v-card>

        </v-menu>

      </template>

    </v-app-bar>

    <!--Conteúdo principal-->
    <v-main>
      <v-container>
        <h1 class="mb-6">Dashboard</h1>

        <!--Tabela-->
        <v-card class="border mb-4">
          <div class="d-flex justify-space-between">
            <v-card-title>Últimos Usuários</v-card-title>

            <v-card-title>Últimos Usuários</v-card-title>

            <!--Caixa de diálogo-->
            <v-card-title>
              <v-btn @click="openDiolog" v-bind="props" variant="tonal" size="smal">Adicionar Usuário</v-btn>
              <v-dialog max-width="600" v-model="isDiologOpen">

                <v-card>
                  <v-card-title>Adicionar Usuário</v-card-title>
                  <v-card-text>
                    <v-row>
                      <v-col>
                        <v-text-field :rules="nomerules" clearable label="Nome" variant="outlined"></v-text-field>

                      </v-col>
                      <v-col>
                        <v-text-field :rules="emailrules" clearable label="E-mail" variant="outlined"></v-text-field>

                      </v-col>
                    </v-row>

                    <v-select :rules="cargorules" label="Cargo" clearable l :items="['Admin', 'Gerente', 'Convidado']"
                      variant="outlined">
                    </v-select>

                  </v-card-text>
                  <v-card-actions>
                    <v-btn variant="tonal" color="red" @click="isDiologOpen = false">Cancelar</v-btn>
                    <v-btn variant="tonal" color="success">Salvar</v-btn>

                  </v-card-actions>
                </v-card>
              </v-dialog>

            </v-card-title>
          </div>

          <v-table>
            <thead>
              <tr>
                <th class="text-left">
                  Nome
                </th>
                <th>
                  E-mail
                </th>
                <th>
                  Cargo
                </th>
                <th>
                  Ações
                </th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Fulano</td>
                <td>fulano@gmail.com</td>
                <td>
                  <v-chip variant="outlined" color="deep-purple-accent-1" size='x-small'>
                    Admin
                  </v-chip>
                </td>
                <td>
                  <v-btn variant="tonal" icon="mdi-pencil" color="orange">

                  </v-btn>
                </td>
              </tr>
              <tr>
                <td>Cicrano</td>
                <td>cigrano@gmail.com</td>
                <td>
                  <v-chip variant="outlined" color="teal-lighten-1" size='x-small'>
                    Gerente
                  </v-chip>
                </td>
                <td>
                  <v-btn variant="tonal" icon="mdi-pencil" color="orange">

                  </v-btn>
                </td>
              </tr>
              <tr>
                <td>Beltrano</td>
                <td>beltrano@gmail.com</td>
                <td>
                  <v-chip variant="outlined" color="yellow-lighten-1" size='x-small'>
                    Usuário
                  </v-chip>
                </td>
                <td>
                  <v-btn variant="tonal" icon="mdi-pencil" color="orange">

                  </v-btn>
                </td>

              </tr>
            </tbody>
          </v-table>
        </v-card>

        <!--Seção de cards-->

        <v-row>
          <!--para entender:
            **O padrão do vuetify é dividir a tela em 12 colunas**
             Para o dispositivos de tela pequena a tela fica divida em 1 coluna;
             Para dispositivos médios a tela é divida em 3 colunas e usamos 4 espaçamentos (4x3=12)
             Para dispositivos grandes a tela é divida em 4 colunas e usamos 3 espaços (3x4 = 12) -->
          <v-col cols="12" sm="6" md="4" lg="3">

            <v-card>
              <v-img class="align-end text-white" max-height="200" cover
                src="https://images.pexels.com/photos/16164299/pexels-photo-16164299/free-photo-of-panorama-vista-paisagem-natureza.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1">
                <v-card-title>
                  Top 10 Lugares no Rio Grande do Sul
                </v-card-title>

              </v-img>
              <v-card-subtitle class="pt-4">Numero 1</v-card-subtitle>
              <v-card-text>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit.</div>
                <div>Voluptates, reiciendis!</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Ver mais" prepend-icon="mdi-plus" variant="outlined"></v-btn>
                <v-btn color="purple-darken-3" text="Comprar" append-icon="mdi-cart" variant="tonal"></v-btn>
              </v-card-actions>

            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card>
              <v-img class="align-end text-white" max-height="200" cover
                src="https://images.pexels.com/photos/16164299/pexels-photo-16164299/free-photo-of-panorama-vista-paisagem-natureza.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1">
                <v-card-title>
                  Top 10 Lugares no Rio Grande do Sul
                </v-card-title>

              </v-img>
              <v-card-subtitle class="pt-4">Numero 1</v-card-subtitle>
              <v-card-text>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit.</div>
                <div>Voluptates, reiciendis!</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Ver mais" prepend-icon="mdi-plus" variant="outlined"></v-btn>
                <v-btn color="purple-darken-3" text="Comprar" append-icon="mdi-cart" variant="tonal"></v-btn>
              </v-card-actions>

            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card>
              <v-img class="align-end text-white" max-height="200" cover
                src="https://images.pexels.com/photos/16164299/pexels-photo-16164299/free-photo-of-panorama-vista-paisagem-natureza.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1">
                <v-card-title>
                  Top 10 Lugares no Rio Grande do Sul
                </v-card-title>

              </v-img>
              <v-card-subtitle class="pt-4">Numero 1</v-card-subtitle>
              <v-card-text>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit.</div>
                <div>Voluptates, reiciendis!</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="orange" text="Ver mais" prepend-icon="mdi-plus"></v-btn>
                <v-btn color="purple-darken-3" text="Comprar" append-icon="mdi-cart" variant="tonal"></v-btn>
              </v-card-actions>

            </v-card>
          </v-col>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card>
              <v-img class="align-end text-white" max-height="200" cover
                src="https://images.pexels.com/photos/16164299/pexels-photo-16164299/free-photo-of-panorama-vista-paisagem-natureza.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1">
                <v-card-title>
                  Top 10 Lugares no Rio Grande do Sul
                </v-card-title>

              </v-img>
              <v-card-subtitle class="pt-4">Numero 1</v-card-subtitle>
              <v-card-text>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit.</div>
                <div>Voluptates, reiciendis!</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Ver mais" prepend-icon="mdi-plus" variant="outlined"></v-btn>
                <v-btn color="purple-darken-3" text="Comprar" append-icon="mdi-cart" variant="tonal"></v-btn>
              </v-card-actions>

            </v-card>
          </v-col>


        </v-row>


      </v-container>


    </v-main>


  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      isDiologOpen: false,
      nomerules: [
        value => {
          if (value) return true

          return 'O campo nome é obrigatório'
        },
      ],
      emailrules: [
        value => {
          if (value) return true;
          return 'O e-mail é obrigatório.'
        },
        value => {
          if (value.includes('@')) {
            return true
          }
          return 'E-mail inválido.'
        }

      ],
      cargorules: [
        value => {
          if (value) return true
          return 'Cargo deve ser selecionado'
        }
      ]
    };
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer
    },
    openDiolog() {
      this.isDiologOpen = !this.isDiologOpen
    }


  },
}
//

</script>
