<template>
<v-app>
    <v-container>
        <v-row>
            <v-col>
                <linechart
                    v-if="loaded"
                    :chartdata="chartdata" 
                    :options="options"></linechart>
                    </v-col>
                </v-row>
    </v-container>

</v-app>
</template>

<script>
import linechart from './chart.js'
import axios from 'axios'
export default {
    name: 'Chartcontents',
    components: {
        linechart
    },
    data: () => ({
        chartdata: null,
        loaded: false,
        options: {
            responsive: true,
            maintainAspectRatio: false
        }
    }),
    async mounted () {
        this.loaded = false
        await axios.get('https://recievetempflaskapi.herokuapp.com/get')
            .then(response => {
		console.log(response.data)
                this.chartdata = {
                    labels: response.data.date,
                    datasets: [
                        {
                            label: 'Temperature',
                            backgroundColor: '#f87979',
                            data: response.data.temp
                        }
                    ],
                }

            })
        this.loaded =true
    }
}
</script>

