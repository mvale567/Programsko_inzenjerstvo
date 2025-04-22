<script setup>
const slike = {
 "Jabuka": "https://www.svgrepo.com/show/530203/apple.svg",
 "Mrkva": "https://www.svgrepo.com/show/530216/carrot.svg",
 "Sir": "https://www.svgrepo.com/show/530219/cake.svg",
 "Kruh": "https://www.svgrepo.com/show/530223/bread.svg",
}

const proizvodi = [
 { naziv: "Jabuka", cijena: 0.25 },
 { naziv: "Mrkva", cijena: 0.12 },
 { naziv: "Kruh", cijena: 2.00 },
 { naziv: "Sir", cijena: 4.48 }
]

const korisnik = {
 jeAdmin: true,
 osobni_podaci: {
    ime: "Marko",
    prezime: "Krivić",
    adresa: {
        grad: "Pula",
        ulica: "Veruda",
        broj: 32
    },
    broj_telefona: "+091-123-456"
 },
 kosarica: [
    { naziv: "Jabuka", količina: 4 },
    { naziv: "Mrkva", količina: 12 },
    { naziv: "Sir", količina: 1 },
    { naziv: "Kruh", količina: 3 },
 ]
}

function dohvati_cijenu(naziv){
    let stavkaID = proizvodi.findIndex(p => p.naziv == naziv)
    if(stavkaID !== -1 ) {
        return proizvodi[stavkaID].cijena}
    return 0   
}

function sveukupna_cijena(){
    let ukupno = 0
    
    for(let i = 0; i < korisnik.kosarica.length; i++){
        let cijena = dohvati_cijenu(korisnik.kosarica[i].naziv)
        let kolicina = korisnik.kosarica[i].količina
        ukupno += cijena * kolicina
    }
    return ukupno
}

function najskupljaStavka(){
    let max_cijena = 0
    let najskuplja = ""
    
    for(let i = 0; i < korisnik.kosarica.length; i++){
        let cijena_proizvoda = dohvati_cijenu(korisnik.kosarica[i].naziv) * korisnik.kosarica[i].količina
        if( cijena_proizvoda > max_cijena){
            max_cijena = cijena_proizvoda
            najskuplja = korisnik.kosarica[i].naziv
        }
    }
    return najskuplja
}

</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-emerald-100 to-green-800 text-gray-800 flex flex-col items-center justify-center gap-10 p-4">

    <div class="bg-white rounded-xl shadow-md p-6 w-[350px]" :class="korisnik.jeAdmin ? 'text-blue-600' : 'text-black'">
      <h2 class="text-xl font-bold mb-2">Korisnički podaci</h2>
      <p>Ime: {{ korisnik.osobni_podaci.ime }} {{ korisnik.osobni_podaci.prezime }}</p>
      <p>Adresa: {{ korisnik.osobni_podaci.adresa.ulica }} {{ korisnik.osobni_podaci.adresa.broj }}, {{ korisnik.osobni_podaci.adresa.grad }}</p>
      <p>Telefon: {{ korisnik.osobni_podaci.broj_telefona }}</p>
    </div>

    <div class="bg-white rounded-xl shadow-md p-6 w-[350px]">
      <h2 class="text-xl font-bold mb-4">Košarica</h2>

        <ul>
            <li>
                <div :class="korisnik.kosarica[0].naziv === najskupljaStavka() ? 'text-red-600' : ''">
                    <img :src="slike[korisnik.kosarica[0].naziv]" class="w-10 h-10" />
                    <p>Naziv proizvod: {{ korisnik.kosarica[0].naziv }}</p>
                    <p>Cijena: {{ dohvati_cijenu(korisnik.kosarica[0].naziv) }} | Količina: {{ korisnik.kosarica[0].količina }}</p>
                    <p>Ukupno: {{ dohvati_cijenu(korisnik.kosarica[0].naziv) * korisnik.kosarica[0].količina}}</p>
                </div>
            </li>
            <li>
                <div :class="korisnik.kosarica[1].naziv === najskupljaStavka() ? 'text-red-600' : ''">
                    <img :src="slike[korisnik.kosarica[1].naziv]" class="w-10 h-10" />
                    <p>Naziv proizvod: {{ korisnik.kosarica[1].naziv }}</p>
                    <p>Cijena: {{ dohvati_cijenu(korisnik.kosarica[1].naziv) }} | Količina: {{ korisnik.kosarica[1].količina }}</p>
                    <p>Ukupno: {{ dohvati_cijenu(korisnik.kosarica[1].naziv) * korisnik.kosarica[1].količina}}</p>
                </div>
            </li>
            <li>
                <div :class="korisnik.kosarica[2].naziv === najskupljaStavka() ? 'text-red-600' : ''">
                    <img :src="slike[korisnik.kosarica[2].naziv]" class="w-10 h-10" />
                    <p>Naziv proizvod: {{ korisnik.kosarica[2].naziv }}</p>
                    <p>Cijena: {{ dohvati_cijenu(korisnik.kosarica[2].naziv) }} | Količina: {{ korisnik.kosarica[2].količina }}</p>
                    <p>Ukupno: {{ dohvati_cijenu(korisnik.kosarica[2].naziv) * korisnik.kosarica[2].količina}}</p>
                </div>
            </li>
            <li>
                <div :class="korisnik.kosarica[3].naziv === najskupljaStavka() ? 'text-red-600' : ''">
                    <img :src="slike[korisnik.kosarica[3].naziv]" class="w-10 h-10" />
                    <p>Naziv proizvod: {{ korisnik.kosarica[3].naziv }}</p>
                    <p>Cijena: {{ dohvati_cijenu(korisnik.kosarica[3].naziv) }} | Količina: {{ korisnik.kosarica[3].količina }}</p>
                    <p>Ukupno: {{ dohvati_cijenu(korisnik.kosarica[3].naziv) * korisnik.kosarica[3].količina}}</p>
                </div>
            </li>
        </ul>

        <p>Ukupna cijena: {{ sveukupna_cijena() }}</p>
    </div>
  </div>
</template>

<style scoped>
</style>
