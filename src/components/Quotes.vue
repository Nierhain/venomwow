<template>
    <v-card height="300px"  justify-center>
        <v-card-title><h3 class="headline font-weight-bold">Best of Venom</h3></v-card-title>
        <v-divider inset light></v-divider>
        <v-card-text id="quotes" class="title">Wenn die Mehrheit dafür ist, wieso soll ich mich dann nicht beugen? - Du kleines Bückstück, du</v-card-text>
    </v-card>
</template>

<script>
export default {
    name: 'Quotes',
    data() {
        return {
            quotes: [
                "Wenn die Mehrheit dafür ist, wieso soll ich mich dann nicht beugen? - Du kleines Bückstück, du",
                "Der Boss kann nix",
                "Da bin ich Mythic Progress geschädet... ähh.. geschädet... ähh geschädigt",
                "Ich mach's dir für 11k",
                "Jaina ist 'ne Grauselbraut. Sylvanas würde ich sofort nehmen",
                "Er ist Freizeit-Österreicher",
                "Wenn ihr euch ins Feuer stellt, sparen wir Mana",
            ]
        }
    },
    mounted() {
        var element = document.getElementById('quotes')
        var counter = 1;
        setInterval(() => {
            element.style.opacity = 0
            setTimeout(() => {
                element.innerHTML = this.quotes[counter]
                element.style.opacity = 1
            }, 500)
            counter++
            if(counter > this.quotes.length){
                counter = 0
            }
        }, 7000)
    }
}
</script>

<style scoped>
#quotes {
    transition: opacity .5s linear;
}
</style>
