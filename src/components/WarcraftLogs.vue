<template>
    <v-layout id="table" justify-center>
        <v-card>
            <v-card-title primary-title>
                <v-flex><v-img :src="`${publicPath}img/logs.png`" :max-height="40" :contain="true"></v-img></v-flex>
                <v-flex><h4>WarcraftLogs</h4></v-flex>
            </v-card-title>
            <v-card-text>
                <div v-show="!reports">
                     <v-progress-circular indeterminate color="primary"></v-progress-circular>
                </div>
                <v-data-table :headers="headers" :items="reports" :pagination.sync="pagination">
                   <template v-slot:items="props">
                       <td>{{props.item.date}}</td>
                       <td><a v-bind:href="props.item.link" target="_blank">{{props.item.title}}</a></td>
                       <td>{{props.item.id}}</td>
                   </template>
                </v-data-table>
            </v-card-text>
        </v-card>
    </v-layout>
</template>

<script>

export default {
    name: "WarcraftLogs",
    data() {
        return {
            publicPath: process.env.BASE_URL,
            reports: [],
            pagination: {'descending' : true},
            headers: [
                {text: 'Datum', value: 'start'},
                {text: 'Link', value: 'title', sortable: false},
                {text: 'Report Code', value: 'id', sortable: false},
            ]
        }
    },
    created() {
        axios.get('https://www.warcraftlogs.com:443/v1/reports/guild/venom/blackhand/eu?api_key=8f995824468221cab7d4198ee0f474d2')
        .then(response => { 
            this.reports = response.data;
            this.reports.forEach(element => {
                element.link = 'https://www.warcraftlogs.com/reports/' + element.id;
                var d = new Date(element.start);
                element.date = d.toLocaleDateString('de-DE');
            })
            });
    }
}
</script>

<style scoped>
    #table {
        margin: 20px;
    }
</style>
