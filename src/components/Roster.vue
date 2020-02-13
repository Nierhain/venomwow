<template>
    <v-container class="text-xs-center">
        <h2 class="display-2 mb-3">Tanks</h2>
        <v-layout row wrap justify-center>
            <v-flex v-for="member in roster.tanks" :key="member" xs1>
                <div >
                    <v-avatar :size="84">
                        <img :src="`${member.avatar}`" alt="">
                    </v-avatar>
                    <div>
                        <a :href="`https://worldofwarcraft.com/de-de/character/eu/blackhand/${member.name}`"><h2>{{member.name}}</h2></a>
                        <v-avatar :size="32">
                            <img :src="`img/class/${member.class}.png`" alt="">
                        </v-avatar>
                    </div>
                </div>
            </v-flex>
        </v-layout>
        <h2 class="display-2 mb-3 mt-5">Heiler</h2>
        <v-layout row wrap justify-center>
            <v-flex v-for="member in roster.healer" :key="member" xs1>
                <div >
                    <v-avatar :size="84">
                        <img :src="`${member.avatar}`" alt="">
                    </v-avatar>
                    <div>
                        <a :href="`https://worldofwarcraft.com/de-de/character/eu/blackhand/${member.name}`"><h2>{{member.name}}</h2></a>
                        <v-avatar :size="32">
                            <img :src="`img/class/${member.class}.png`" alt="">
                        </v-avatar>
                    </div>
                </div>
            </v-flex>
        </v-layout>
        <h2 class="display-2 mb-3 mt-5">DPS</h2>
        <v-layout row wrap justify-center>
            <v-flex v-for="member in roster.dps" :key="member" xs3>
                <div >
                    <v-avatar :size="84" >
                        <img :src="`${member.avatar}`" alt="">
                    </v-avatar>
                    <div class="mb-4">
                        <a :href="`https://worldofwarcraft.com/de-de/character/eu/blackhand/${member.name}`"><h2>{{member.name}}</h2></a>
                        <v-avatar :size="32">
                            <img :src="`img/class/${member.class}.png`" alt="">
                        </v-avatar>
                    </div>
                </div>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import roster from '@/Roster.js'
import config from '@/config.json'
export default {
    name: 'Roster',
    data() {
        return {
            publicPath: process.env.BASE_URL,
            roster,
            rolenames: [
                "Tanks",
                "Heiler",
                "DPS"
            ]
        }
    },
    mounted() {
        const querystring = require('querystring')
        let access_token
        axios.post('https://eu.battle.net/oauth/token', querystring.stringify({client_id: config.CLIENT_ID, client_secret: config.CLIENT_SECRET, grant_type: 'client_credentials'}))
            .then(response => {
                access_token = response.data.access_token

                this.roster.tanks.forEach(member => {
                    axios.get('https://eu.api.blizzard.com/wow/character/blackhand/' + member.name + '?locale=de_DE&access_token=' + access_token).then(response =>{
                        member.avatar = "https://render-eu.worldofwarcraft.com/character/"+ response.data.thumbnail
                        member.class = response.data.class
                    })
                })
                
                this.roster.healer.forEach(member => {
                    axios.get('https://eu.api.blizzard.com/wow/character/blackhand/' + member.name + '?locale=de_DE&access_token=' + access_token).then(response =>{
                        member.avatar = "https://render-eu.worldofwarcraft.com/character/"+ response.data.thumbnail
                        member.class = response.data.class
                    })
                })

                this.roster.dps.forEach(member => {
                    axios.get('https://eu.api.blizzard.com/wow/character/blackhand/' + member.name + '?locale=de_DE&access_token=' + access_token).then(response =>{
                        member.avatar = "https://render-eu.worldofwarcraft.com/character/"+ response.data.thumbnail
                        member.class = response.data.class
                    })
                })
                
            });
                              

    }
}
</script>

<style scoped>
a{
    text-decoration: none;
}
</style>
