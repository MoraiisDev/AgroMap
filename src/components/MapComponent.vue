<template>
  <div style="height:700px; width:700px;">
    <l-map ref="map" 
    :zoom="4"
    :center="[-14.235, -51.9253]"
    :maxBounds="maxBounds"
    :maxZoom="7"
    :minZoom="4">

    <l-tile-layer
      url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
      layer-type="base"
      name="OpenStreetMap"
    ></l-tile-layer>

    <l-circle-marker
      v-for="(circle, index) in circles"
      :key="'circle-' + index"
      :lat-lng="circle.center"
      :radius="circle.radius"
      :color="circle.color"
    >
      <l-popup>
        <span>{{ circle.popupContent }}</span>
      </l-popup>
    </l-circle-marker>
    </l-map>
  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import { LMap, LTileLayer, LCircleMarker, LPopup } from "@vue-leaflet/vue-leaflet";

export default {
  components: {
    LMap,
    LTileLayer,
    LCircleMarker,
    LPopup,
  },

  data() {
    return {
       maxBounds: [
         [-33.75, -73.98], // Sudoeste do Brasil
         [5.27, -34.79],   // Nordeste do Brasil
       ],
       circles: [ 
         { 
           center: [-2.811371, -58.886719],
           radius: 110,
           color: 'green',
           popupContent: 'É a área onde a expansão das atividades agrárias ocorre mais intensamente, o que torna a região Norte como o futuro centro de crescimento do agronegócio brasileiro. As atividades mais praticadas nessa região ainda são de caráter extensivo e de busca por tecnologia, o que o torna um mercado promissor e de crescimento acelerado. Principais produtos do Norte do país: Soja, mandioca, milho, açaí, cacau, banana e fibras',
          },
          { 
            center: [-8.05923, -40.209961],
            radius: 80,
            color: 'red',
            popupContent: 'A região Nordeste seja, talvez, uma das regiões agrícolas com maior pluralidade. Isso porque, nas áreas semiáridas, ressaltamos a presença da agricultura familiar. Principais produtos da Região Nordeste: Cana-de-açúcar, soja, milho, algodão, cacau, frutas (banana, manga, maracujá, laranja, melancia, abacaxi, uva)',
          },
          { 
           center: [-16.762468, -52.646484],
           radius: 65,
           color: 'orange',
           popupContent: 'A Revolução Verde, expressão que se refere à invenção e disseminação de novas sementes e práticas agrícolas que aumentam a produção, foi responsável pela ocupação dos solos do Cerrado nesta região. Ela permitiu o cultivo de diversas culturas em seus solos de elevada acidez. Principais produtos da Região Centro-Oeste: Soja, milho, cana-de-açúcar, algodão, arroz, carne bovina, carne de aves, feijão e ovos de galinha',
          },
        {
         center: [-20.632784, -44.912109],
         radius: 40,
         color:'yellow',
         popupContent: 'Apesar de a agricultura encontrar-se mais subordinada à indústria, é importante destacar também os altos índices de produtividade e o excelente solo nesta região. Principais produtos da Região Sudeste: Café, cana-de-açúcar, laranja, tomate, milho e hortaliças',
          },
        { 
         center: [-27.722436, -51.240234],
         radius: 30,
         color: 'blue',
         popupContent: 'É importante destacar que a agricultura da região Sul desempenha um papel principal. Isso porque, a produção da soja se tornou um produto de extirpação, antes, era voltada apenas para o mercado regional. Principais da Região Sul do país: Soja, arroz, milho, trigo, fumo, uva, maçã, cana-de-açúcar, mandioca, feijão e erva-mate',
        },
      ],
    };
  },
}
</script>