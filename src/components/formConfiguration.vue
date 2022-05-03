<template>
  <div class="flex justify-center m-8">
    <section class="font-semibold">
      <h1>Configuration :</h1>
      <ul>
        Modifier les options de recherche :
        <li>Nom <input type="checkbox" /></li>
        <li>Ecole <input type="checkbox" /></li>
        <li>Classe <input type="checkbox" /></li>
        <li>Branche <input type="checkbox" /></li>
      </ul>
    </section>
  </div>
</template>


<script>
export default {
  name: "ongletConfiguration",
};

// //Permet de sauvegarder la conf
// var fs = require("fs");

// var myConf = {
//   nomConf: true,
//   ecoleConf: true,
//   classeConf: true,
//   brancheConf: true,
// };

// var confSave = JSON.stringify(myConf); //transforme en JSON

// fs.writeFile("./config.json", data, function (err) {
//   if (err) {
//     console.log("Erreur lors de la sauvegarde");
//   } else {
//     console.log("Sauvegarde effectuée");
//   }
// });
</script>