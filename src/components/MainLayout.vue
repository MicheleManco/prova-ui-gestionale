<template>
<div id="container">
  
  <div class="btn-group">
    <!-- bottone indirizzo  -->
    <button type="button" class="btn btn-light dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false"><strong>INDIRIZZO </strong></button>
    <ul class="dropdown-menu">
      <li class="dropdown-item"> Destinatario: {{aziende[countervisible].ordine.indirizzo.nome}} , {{aziende[countervisible].ordine.indirizzo.cognome}}</li>
      <li class="dropdown-item">Indirizzo: {{aziende[countervisible].ordine.indirizzo.indirizzo1}} , {{aziende[countervisible].ordine.indirizzo.cap}} {{aziende[countervisible].ordine.indirizzo.citta}}</li>
      <li class="dropdown-item">{{aziende[countervisible].ordine.indirizzo.nazione}},{{aziende[countervisible].ordine.indirizzo.telefono}}</li>
    </ul>

    <!-- bottone ordine  -->
    <button type="button" class="btn btn-light dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false"><strong>ORDINE </strong></button>
    <ul class="dropdown-menu">
      <li class="dropdown-item">{{aziende[countervisible].ordine.ecommerceProvenienza}} , {{aziende[countervisible].ordine.data}}</li>
      <li class="dropdown-item">{{aziende[countervisible].ordine.corriere}} , {{aziende[countervisible].ordine.idOrdine}}</li>
      <li class="dropdown-item">Pagamento: {{aziende[countervisible].ordine.pagamento}} , Valuta: {{aziende[countervisible].ordine.valuta}}</li>
      <li class="dropdown-item">Totale prodotti: {{aziende[countervisible].ordine.totProdotti}}€</li>
      <li class="dropdown-item">Totale sconto: {{aziende[countervisible].ordine.totSconto}}€</li>
      <li class="dropdown-item">Totale spedizione: {{aziende[countervisible].ordine.totSpedizione}}€</li>
      <li class="dropdown-item">Totale incasso: {{aziende[countervisible].ordine.totIncasso}}€</li>
    </ul>

    <!-- bottone cliente  -->
    <button type="button" class="btn btn-light dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false"><strong>CLIENTE </strong></button>
    <ul class="dropdown-menu">
      <li class="dropdown-item">{{aziende[countervisible].ordine.cliente.nome}} , {{aziende[countervisible].ordine.cliente.cognome}}</li>
      <li class="dropdown-item">{{aziende[countervisible].ordine.cliente.email}} </li>
      <li class="dropdown-item">Sesso: {{aziende[countervisible].ordine.cliente.sesso}}</li>
    </ul>

    <!-- stato ordine ------------------------------------------------------------------------------------------------------------>
    <button type="button" class="btn btn-light dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false"><strong>STATO ORDINE </strong></button>
    <ul class="dropdown-menu">
      <li class="dropdown-item">

        <div class="avanzamento">
          <div class="step">
            <div><h6>spedito</h6></div>
            <div class="dot"><i class="bi bi-building"></i></div>
          </div> 
          <div class="step in-consegna">
            <div><h6>in consegna</h6></div>
            <div class="dot"><i class="bi bi-arrow-counterclockwise"></i></div>
          </div> 
          <div class="step">
            <div><h6>consegnato</h6></div>
            <div class="dot"><i class="bi bi-house-door"></i></div>
          </div>
        </div>
        <!-- barra di stato  -->
        <div class="progress">
          <div class="progress-bar progress-bar-striped progress-bar-animated" role="progressbar" :aria-valuenow="aziende[countervisible].ordine.statoOrdine" aria-valuemin="0" aria-valuemax="100" :style="`width:${aziende[countervisible].ordine.statoOrdine}%`"></div>
        </div>
      </li>

      <li class="dropdown-item">
        Spedito da:
      </li>
      <li class="dropdown-item">
        Arrivato a:
      </li>
      <li class="dropdown-item">
        Consegnato a:
      </li>
    </ul>

    <!-- btn note -------------------------------------------------------------------------------------->
    <p>      
      <button class="btn btn-light dropdown-toggle" type="button" data-bs-toggle="collapse" data-bs-target=".multi-collapse" aria-expanded="false" aria-controls="multiCollapse1 multiCollapse2"><strong>NOTE</strong> </button>
    </p>
    <div class="row riga-note">
      <div class="col-6">
        <div class="collapse multi-collapse" id="multiCollapse1">
          <div class="card card-body">
            <h5>Operatore:</h5><div class="note">{{aziende[countervisible].ordine.noteOrdine.operatore}} </div><br>
            <h5> Nota:</h5> <div class="note">{{aziende[countervisible].ordine.noteOrdine.text}}</div>
          </div>
        </div>
      </div>
      
      <div class="col-6">
        <div class="collapse multi-collapse" id="multiCollapse2">
          <div class="card card-body">
            <h5>Cliente:</h5>  <div >{{aziende[countervisible].ordine.noteCliente.cliente}}</div> <br>
            <h5>Nota:</h5> <div >{{aziende[countervisible].ordine.noteCliente.text}}</div> 
          </div>
        </div>
      </div>
    </div>
  </div>

  <!----------------------------------------------------------------------------------------------------------------------------------------------->

  <!-- riquadro prodotti  -->
  <div id="background-white">
    <!-- qui andranno i prodotti  -->
    <ul>
      <li class="product" v-for="prodotto,i in aziende[countervisible].ordine.prodotti" :key="i" >
        <div class="anteprima-prodotto"><img :src="require(`../${prodotto.img}`)" alt=""></div>  
        
        <div class="spaziatore">
          <div class="title-prod">
            <div><h4>{{prodotto.nome}}: {{prodotto.skulLocation}}</h4></div> 
            <div>Prezzo unitario: {{prodotto.prezzo}}€ </div>
          </div>
          <div class="info-prod">
            <div>Q. Aquistata: {{prodotto.quantitaAcquistata}}pz</div> 
            <div>Q. Rimanente: {{prodotto.quantitaRimanente}}pz</div> 
          </div>
        </div>

      </li>
    </ul>
  </div>

  <!----------------------------------------------------------------------------------------------------------------------------------------------->

  <!-- parte bassa con tasto chiusura ordine  -->
  <div id="btn-finali">
    <button class="btn btn-scatola"><strong>Scegli Scatola</strong></button>
    <button class="btn btn-success"><strong>Chiusura Ordine</strong></button>
  </div>
  
</div>

</template>

<script>
export default {
  name: 'MainLayout',
  data(){
      return{

      }
  },
  props:{
      aziende:Array,//questo è tutto l'array di dati che ho
      countervisible:Number//questa è una variabile numerica che cambia il suo valore in base al click
  },
}
</script>


<style scoped lang="scss">
/* Hide scrollbar for Chrome, Safari and Opera */
#container::-webkit-scrollbar {
    display: none;
}
/* Hide scrollbar for IE, Edge and Firefox */
#container {
-ms-overflow-style: none;  /* IE and Edge */
scrollbar-width: none;  /* Firefox */
}
#container{
  width: 76%;
  background-color: #cacaca;
  max-height: 95vh;
  border-radius: 15px;
  padding:8px;
  box-shadow: 0px 8px 17px 2px rgba(0,0,0,0.14) , 0px 3px 14px 2px rgba(0,0,0,0.12) , 0px 5px 5px -3px rgba(0,0,0,0.2);
  overflow: scroll;
  .btn-group{
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    .riga-note{
      min-width: 800px;
    }
    .card-body{
      max-width: 450px;
      margin: 10px 10px;
      box-shadow: 0px 2px 5px 0px rgba(0,0,0,0.14) , 0px 1px 10px 0px rgba(0,0,0,0.12) , 0px 2px 4px -1px rgba(0,0,0,0.2);
    }
    .btn{
      margin: 20px;
      padding: 0px 20px;
      border-radius: 40px;
      height: 70px;
      background-color: #e6e6e6;
      box-shadow: -2px -4px 0px 0px #0006 inset, 2px 2px 0px 0px #FFF7 inset;
    }
  }
  /* Hide scrollbar for Chrome, Safari and Opera */
  #background-white::-webkit-scrollbar {
      display: none;
  }
  /* Hide scrollbar for IE, Edge and Firefox */
  #background-white {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
  }
  #background-white{
    max-height: 67%;
    margin: 0 20px;
    padding: 0 20px;
    border-radius: 20px;
    box-shadow: 4px 8px 11px 6px rgba(0,0,0,0.14) , 4px 5px 14px 4px rgba(0,0,0,0.12) , 4px 6px 8px 3px rgba(0,0,0,0.2);
    background-color: white;
    overflow: scroll;
    .product{
      list-style: none;
      border-radius: 10px;
      padding: 10px;
      margin: 20px 0px;
      background-color: #e6e6e6;
      box-shadow: 0px 2px 5px 0px rgba(0,0,0,0.14) , 0px 1px 10px 0px rgba(0,0,0,0.12) , 0px 2px 4px -1px rgba(0,0,0,0.2);
      display: flex;
      align-items: center;
      .spaziatore{
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 22px;
        .title-prod{
          margin:0 30px;
        }
        .info-prod{
          margin-right: 80px;
        }
      }
      
      .anteprima-prodotto{
        width: 100px;
        img{
          border-radius: 10px;
          max-width: 100%;
          max-height: 100%;
          
          box-shadow: 0px 2px 5px 0px rgba(0,0,0,0.14) , 0px 1px 10px 0px rgba(0,0,0,0.12) , 0px 2px 4px -1px rgba(0,0,0,0.2);
        }
      }
    }
  }
  .avanzamento{
    display: flex;
    justify-content: space-between;
    .in-consegna{
      padding-left: 10px;
    }
    .step{
      margin:0 25px;
      display: flex;
      flex-direction: column;
      align-items: center;
      .dot{
        font-size: 20px;
        margin:5px 0 10px;
      }
    }
  }
  #btn-finali{
    display: flex;
    justify-content: space-around;
    margin: 40px 0;
    .btn-scatola{
        background-color: #ffa500;
        color: white;
      }
    .btn{
      height: 70px;
      width: 200px;
      border-radius: 10px;
      box-shadow: -2px -4px 0px 0px #0006 inset, 2px 2px 0px 0px #FFF7 inset;
    }
  }
}
</style>