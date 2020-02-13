<template>
    <v-container align-content-center>
        <v-container grid-list-xl fluid mb-5>
            <h3 class="headline text-uppercase text-xs-center mb-5">Gildenleitung</h3>
            <v-layout row wrap justify-center>
                <v-flex v-for="n in leaders.slice(0,3)" :key="n" xs4>
                    <v-card>
                        <v-img :src="n.imageurl"></v-img>
                        <v-card-title><v-spacer></v-spacer><span class="title text-xs-center text-uppercase">{{n.name}} - {{n.position}}</span><v-spacer></v-spacer></v-card-title>
                    </v-card>
                </v-flex>
            </v-layout>
        </v-container>
    </v-container>
</template>

<script>
import config from '../config.json'
export default {
    name: 'Leaders',
    data() {
        return {
            leaders: [
                {
                    "name" : "Nierpal",
                    "imageurl": "",
                    "position": "Stellvertreter"
                },
                {
                    "name" : "Buliwyff",
                    "imageurl": "",
                    "position": "Gildenmeister"
                },
                {
                    "name" : "Trenga",
                    "imageurl": "",
                    "position": "Raidlead"
                }
            ]
        }
    },
    mounted() {
        const querystring = require('querystring')
        let access_token
        axios.post('https://eu.battle.net/oauth/token', querystring.stringify({client_id: config.CLIENT_ID, client_secret: config.CLIENT_SECRET, grant_type: 'client_credentials'}))
        .then(res => {
            access_token = res.data.access_token

            this.leaders.forEach(el => {
            axios.get('https://eu.api.blizzard.com/wow/character/blackhand/' + el.name + '?locale=de_DE&access_token=' + access_token)
            .then(response =>{
                el.imageurl = "https://render-eu.worldofwarcraft.com/character/"+ response.data.thumbnail.replace('-avatar.jpg','-main.jpg')
            });
        })
        });

    }
}
</script>
