<template>
    <v-container grid-list-m>
        <v-layout row wrap>
            <v-flex xs4 offset-xs4>
                <v-card flat class="mt-5">
                    <v-card-title><h2>Was hat es mit diesem M+ Stein Channel auf sich?</h2></v-card-title>
                    <v-card-text><p>Ihr kennt bestimmt diesen Moment am Sonntag, an dem es heißt "Wer hat welchen Stein? Was spielen wir? Ich würde gerne Stein X laufen". Deshalb haben wir uns gedacht, erstellen wir einfach einen Chatkanal, in dem ihr alle eure dieswöchigen/aktuellen M+ Steine posten könnt, um euch in eurer Lieblingsinstanz zusammen zu finden und es Leuten, die andere in Gruppen schieben, einfach macht, die richtigen Leute in die richtigen Steinchen zu stecken. <br><br>In diesem Kanal werden ausschließlich M+ Steine gepostet. Ihr führt da drin <em><b>KEINE</b></em> Unterhaltungen oder sonstiges.</p></v-card-text>
                    <v-card-title><h3>Und wie genau mach ich das jetzt?</h3></v-card-title>
                    <v-card-text><p>Alles ganz einfach:</p>
                                <br><v-img :src="`${publicPath}img/guide/chat.jpg`"></v-img>
                                <p>Zuerst öffnet ihr das Gildenfenster. Sollte es nicht schon ausgewählt sein, klickt auf den Chat</p> 
                                <br><v-img :src="`${publicPath}img/guide/guild.jpg`"></v-img>
                                <p>Dann klickt ihr oben auf den Pfeil neben dem aktuellen Chatkanal. Standardmäßig steht hier Gilde bei euch (Bei mir steht dort Guild, da ich den englischen Client benutze)</p>
                                <v-img :src="`${publicPath}img/guide/channel.jpg`"></v-img>
                                <p>Nun wählt ihr einfach "M+ Steine" aus der Dropdown-Liste aus.</p>
                                <v-img :src="`${publicPath}img/guide/add.jpg`"></v-img>
                                <p>Zu guter Letzt könnt ihr hier nun diesen Kanal an euren aktuellen Chat Tab anfügen oder einen neuen dafür erstellen. Wenn ihr diese Option benutzt, wird auch der Kanal in eurem normalen Chat angezeigt</p>
                    </v-card-text>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    data() {
        return {
            publicPath: process.env.BASE_URL
        }
    }
}
</script>
