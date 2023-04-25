<template>
  <div class="main-container">
  <v-data-table
     id="table"
    :headers="headers"
    :items="entradas"
    sort-by="nome"
    
  >
    <template v-slot:top>
      <v-toolbar
        flat
      >
        <v-toolbar-title><h4>Depoimentos</h4></v-toolbar-title>
        <v-divider
          class="mx-4"
          inset
          vertical
        ></v-divider>
        <v-spacer></v-spacer>
        <v-dialog
          v-model="dialog"
          max-width="500px"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="primary"
              dark
              class="mb-2"
              v-bind="attrs"
              v-on="on"
            >
              Novo Depoimento
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">{{ formTitle }}</span>
            </v-card-title>

            <v-card-text>
              <v-container>
                <v-row>
                  <v-col
                    cols="12"
                    
                  >
                    <v-text-field
                      v-model="editedItem.title"
                      label="Nome"
                    ></v-text-field>
                  </v-col>
                  <!--<v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.nome"
                      label="Data"
                    ></v-text-field>
                  </v-col> -->
                 <!-- <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                  <v-text-field
                      v-model="editedItem.email"
                      label="Id"
                    ></v-text-field>
                  </v-col> -->
                  <!--<v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.assunto"
                      label="assunto"
                    ></v-text-field>
                  </v-col>-->
                  <v-col
                    cols="12"
                    
                  >
                    <v-text-field
                      v-model="editedItem.content"
                      label="Mensagem"
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="blue darken-1"
                text
                @click="close"
              >
                Cancelar
              </v-btn>
              <v-btn
                color="blue darken-1"
                text
                @click="save"
              >
                Confirme
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <v-dialog v-model="dialogDelete" max-width="500px">
          <v-card>
            <v-card-title class="text-h5">Deseja excluir este depoimento?</v-card-title>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="closeDelete">Cancelar</v-btn>
              <v-btn color="blue darken-1" text @click="deleteItemConfirm">Confirme</v-btn>
              <v-spacer></v-spacer>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>
    </template>
    <template v-slot:item.actions="{ item }">
      
      <v-icon
  class="mr-2"
  @click="editItem(item)"
  color="blue"
>
  mdi-pencil
</v-icon>
<v-icon
  @click="deleteItem(item)"
  color="red"
>
  mdi-delete
</v-icon>
    </template>
    <template v-slot:no-data>
      <v-btn
        color="primary"
        @click="initialize"
      >
        Reset
      </v-btn>
    </template>
  </v-data-table>
</div >
</template>

<script>
  export default {
    data: () => ({
      config:{
        headers:{
          Authorization:'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0L3dvcmRwcmVzcy1hcGkvdGVzdGFwaXdvcmRwcmVzcyIsImlhdCI6MTY4MjEwMDI5MSwibmJmIjoxNjgyMTAwMjkxLCJleHAiOjE2ODI3MDUwOTEsImRhdGEiOnsidXNlciI6eyJpZCI6IjEifX19.3wisJcf2hIqe11GinQ3GYoOIXJ_L1ANOKdHLtWqsp_A'
        }
      },
      dialog: false,
      dialogDelete: false,
      headers: [
        {
          text: 'Nome',
          align: 'start',
          sortable: false,
          value: 'title',
        },
        { text: 'Data ', value: 'date' },
        { text: 'Id', value: 'id' },
        { text: 'Mensagem ', value: 'content' },
        { text: 'Status ', value: 'status' },
        { text: 'Actions', value: 'actions', sortable: false },
      ],
      entradas: [],
      editedIndex: -1,
      editedItem: {
        title: '',
        id:'' ,
        content: '',
        date:'',
        status:'',
      },
      defaultItem: {
        title: '',
        id: '',
        content: '',
        status:'',
      },
    }),

    computed: {
      formTitle () {
        return this.editedIndex === -1 ? 'Novo Depoimento' : 'Edição de Depoimento'
      },
    },

    watch: {
      dialog (val) {
        val || this.close()
      },
      dialogDelete (val) {
        val || this.closeDelete()
      },
    },

    created () {
      this.initialize()
    },

    methods: {
      clear(value){
  return value.replace(/<\/?[^>]+(>|$)/g, "")
},

     async initialize () { 
        
    
      try{
        const entradaDB = await this.axios.get ('wp/v2/posts');
        //console.log(entradaDB.data);
        await entradaDB.data.forEach(element => {
        //console.log(element)
        let item = {}
        item.id = element.id;
        item.title = element.title.rendered;
        item.content = this.clear(element.content.rendered);
        item.date = element.date;
        item.status = element.status;
        this.entradas.push(item)
        });

      } catch (error) {
        console.log(error);
      }
    
      },

      editItem (item) {
        this.editedIndex = this.entradas.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialog = true
      },

      async deleteItem (item) {
        this.editedIndex = this.entradas.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialogDelete = true

        
          await this.axios.delete(`wp/v2/posts/${item.id}`,this.config)
        
      },

      deleteItemConfirm () {
        this.entradas.splice(this.editedIndex, 1)
        this.closeDelete()
      },

      close () {
        this.dialog = false
        this.$nextTick(() => {
          this.editedItem = Object.assign({}, this.defaultItem)
          this.editedIndex = -1
        })
      },

      closeDelete () {
        this.dialogDelete = false
        this.$nextTick(() => {
          this.editedItem = Object.assign({}, this.defaultItem)
          this.editedIndex = -1
        })
      },

     async save () {
        if (this.editedIndex > -1) {
          
          //edit
          console.log(this.editedItem);

          try {
            const entradaEditada = await this.axios.post(`wp/v2/posts/${this.editedItem.id}`,this.editedItem,this.config)
            Object.assign(this.entradas[this.editedIndex], this.editedItem)
          } catch (error) {
            console.log(error)
          }

        } else {

        //save
          console.log(this.editedItem);

          const entrada = {
            title: this.editedItem.title,
            content: this.editedItem.content,
            status:'publish'
          }

          try {
            const entradaDB = await this.axios.post('wp/v2/posts', entrada, this.config)
          console.log(entradaDB.data);

          this.editedItem.id = entradaDB.data.id;
          this.editedItem.date = entradaDB.data.date;
          this.editedItem.status = entradaDB.data.status;

          this.entradas.push(this.editedItem)
            
          } catch (error) {
            console.log(error)
            
          }

          
        }
        this.close()
      },
    },
  }
</script>

<style lang="scss" scoped>
#table{
  background-color: #ffffff;
    padding:  50px 70px;
    justify-content: flex-end;
    align-items: center;
    border-bottom: 1px solid #2420205e;
}

</style>