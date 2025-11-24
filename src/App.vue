<template>
  <TopBar />
  <RouterView />
</template>

<script setup>
import { RouterView } from 'vue-router';
import TopBar from './components/Header.vue';
import { ref, provide } from 'vue';
import  ramen  from './assets/images/ramen.jpg';
import tacos from './assets/images/tacos.jpg';
import risotto from './assets/images/rissotto.jpg';
import salmoMarinat from './assets/images/poke.jpg';
import espaguetti from './assets/images/espaguetti.jpg';
import galetaXocolata from './assets/images/galeta.jpg';

const receptes = ref([
  {
    id: 1,
    nom: 'Ramen aromàtic de miso',
    descripcio:
      'Brou profund amb miso, fideus de blat, verdures cruixents i ou marinat.',
    ingredients: [
      'Fideus de ramen',
      'Brou de pollastre o verdura',
      'Pasta de miso',
      'Xitakes',
      'Ceba tendra',
      'Ou marinat',
      'Oli de sèsam'
    ],
    passos: [
      'Escalfa el brou i incorpora-hi la pasta de miso fins que es dissolgui.',
      'Salteja els bolets amb una mica d’oli de sèsam.',
      'Cou els fideus segons les indicacions del paquet.',
      'Munta el bol amb fideus, brou, bolets, ceba tendra i mig ou marinat.'
    ],
    img: ramen,
    puntuacio: 5
  },
  {
    id: 2,
    nom: 'Tacos de verdures rostides',
    descripcio:
      'Tortilles de blat de moro farcides amb verdures al forn i salsa fresca.',
    ingredients: [
      'Tortilles de blat de moro',
      'Pebrot vermell',
      'Carbassó',
      'Ceba morada',
      'Alvocat',
      'Llimona',
      'Coriandre fresc'
    ],
    passos: [
      'Talla les verdures i rostix-les al forn amb oli, sal i pebre.',
      'Escalfa lleugerament les tortilles.',
      'Omple les tortilles amb les verdures rostides.',
      'Afegeix daus d’alvocat, suc de llimona i coriandre picat per sobre.'
    ],
    img: tacos,
    puntuacio: 4
  },
  {
    id: 3,
    nom: 'Risotto de bolets i parmesà',
    descripcio:
      'Arròs cremós cuinat lentament amb bolets, vi blanc i formatge parmesà.',
    ingredients: [
      'Arròs arborio',
      'Bolets variats',
      'Ceba',
      'Brou calent',
      'Vi blanc',
      'Parmesà ratllat',
      'Mantega'
    ],
    passos: [
      'Sofregeix la ceba picada amb una mica de mantega fins que sigui transparent.',
      'Afegeix l’arròs i torra’l uns minuts.',
      'Aboca-hi el vi blanc i deixa que evapori.',
      'Vés afegint brou calent a poc a poc, remenant fins que l’arròs sigui cremós.',
      'Incorpora els bolets saltejats i el parmesà ratllat abans de servir.'
    ],
    img: risotto,
    puntuacio: 5
  },
  {
    id: 4,
    nom: 'Bowl de salmó marinat',
    descripcio:
      'Bol d’arròs amb salmó marinat, verdures fresques i salsa de soja dolça.',
    ingredients: [
      'Llom de salmó fresc',
      'Arròs de gra curt',
      'Cogombre',
      'Pastanaga',
      'Alga nori',
      'Salsa de soja',
      'Mel o mirin'
    ],
    passos: [
      'Marina el salmó amb salsa de soja i mel durant uns 20 minuts.',
      'Cou l’arròs i deixa’l temperar lleugerament.',
      'Talla el cogombre i la pastanaga en bastonets fins.',
      'Munta el bol amb arròs, salmó, verdures i tires d’alga nori.'
    ],
    img: salmoMarinat,
    puntuacio: 4
  },
  {
    id: 5,
    nom: 'Espaguetis carbonara (amb guanciale)',
    descripcio:
      'Pasta tradicional italiana amb guanciale, pecorino i una salsa d\'ou cremosa i sedosa.',
    ingredients: [
      '400 g espaguetis (o altra pasta llarga)',
      '150–200 g guanciale tallat a tires o daus',
      '3 ous sencers + 1 rovell (o 4 rovells si prefereixes)',
      '100 g Pecorino Romano ratllat finament',
      'Pebre negre mòlt fresc (a gust)',
      'Sal per a l\'aigua de cocció (modera)',
      '100–200 ml aigua de cocció de la pasta (reservada)'
    ],
    passos: [
      "Porta una olla gran amb aigua a bullir i sala lleugerament.",
      'Talla el guanciale a tires o daus d\'uns 1 cm.',
      'Fes coure el guanciale en una paella a foc mitjà-baix fins que el greix s\'estovi i la carn quedi daurada i cruixent (5–8 min). Reserva la paella amb el greix.',
      'Bat els 3 ous sencers i l\'1 rovell amb el Pecorino i una bona quantitat de pebre negre fins obtenir una barreja homogènia.',
      'Cuina la pasta al dente segons el paquet; reserva 100–200 ml de l\'aigua de cocció abans d\'escórrer.',
      'Afegeix la pasta escorreguda a la paella amb el guanciale amb el foc APAGAT o molt baix.',
      "Fora del foc, aboca la barreja d\'ous i formatge sobre la pasta i remena ràpidament perquè l\'ou s\'emulsioni i formi una salsa sedosa.",
      'Si la salsa queda massa espessa, ajusta amb una mica d\'aigua de cocció calenta fins a la textura desitjada; no posis la paella a foc directe per evitar quallar l\'ou.',
      'Prova i rectifica amb més pebre negre i, si cal, una mica més de Pecorino. Serveix immediatament.'
    ],
    img: espaguetti,
    puntuacio: 5
  },
  {
    id: 6,
    nom: 'Galeta gegant de xocolata',
    descripcio:
      'Galeta de forn gruixuda, tova al centre i plena de trossets de xocolata.',
    ingredients: [
      'Farina',
      'Mantega',
      'Sucre blanc',
      'Sucre morè',
      'Ous',
      'Xips de xocolata',
      'Llevat químic',
      'Sal en escates'
    ],
    passos: [
      'Barreja la mantega amb els sucres fins obtenir una crema.',
      'Incorpora els ous i després la farina amb el llevat.',
      'Afegeix els xips de xocolata i forma una massa compacta.',
      'Estén la massa en forma de disc gruixut i enforna fins que les vores siguin daurades.',
      'En sortir del forn, acaba amb unes escates de sal per sobre.'
    ],
    img: galetaXocolata,
    puntuacio: 5
  }
]);

const productes = ref([
  { id: 1, nom: 'iPhone 13', preu: 499 },
  { id: 2, nom: 'Teclat Logitech K380', preu: 42 },
  { id: 3, nom: 'Ratolí Logitech M185', preu: 12 },
  { id: 4, nom: 'Samsung Galaxy A34', preu: 249 },
  { id: 5, nom: 'Micròfon Fifine K669', preu: 39 },
  { id: 6, nom: 'Auriculars Sony WH-CH520', preu: 59 }
]);


const carret = ref([{ id: 2, nom: 'Teclat Logitech K380', preu: 42 }]);

provide('productes', productes);
provide('carret', carret);
provide('receptes', receptes);
</script>

<style scoped></style>
