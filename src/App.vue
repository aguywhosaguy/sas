<script>
var unsortedores = [{name: 'coal', av: 275000, cv: 1, amount: 0},
{name: 'diamond', av: 275000, cv: 3, amount: 0},
{name: 'troll', av: 275000, cv: 4, amount: 0}
]
    export default {
        data() {
            return {
                ores: unsortedores.sort(function(a, b) {return a.cv - b.cv}),
                totalcv: 0,
                totalav: 0
            }
            
        },
        
        watch: {
            ores: {
                deep: true,
                handler() {
                    this.totalcv = 0
                    this.totalav = 0
                    for (var i = 0; i < this.ores.length; i++) {
                        console.log(this.totalcv)
                        this.totalcv += this.ores[i].cv * this.ores[i].amount
                        this.totalav += this.ores[i].av * this.ores[i].amount
                    }
                }
            }
        }
    }

</script>

<template>
    <div class="tables">
        <table>
            <tr>
                <th>Ore</th>
                <th>Amount</th>
            </tr>
            <tr v-for="ore in ores" :key="ore.cv">
                <td>{{ ore.name }}</td>
                <td class="small">
                    <input type="number" v-model="ore.amount" maxlength="5"/>
                </td>
            </tr>
        </table>
        <table>
            <tr>
                <th>Ore</th>
                <th>AV</th>
                <th>CV</th>
                <th>Amount</th>
            </tr>
            <tr>
                <td>{{ totalcv }}</td>
                <td>{{ totalav }}</td>
            </tr>
            <tr>
                <td>{{ totalcv }}</td>
                <td>{{ totalav }}</td>
            </tr>
            <tr>
                <td>{{ totalcv }}</td>
                <td>{{ totalav }}</td>
            </tr>
            <tr>
                <td>{{ totalcv }}</td>
                <td>{{ totalav }}</td>
            </tr>
            <tr>
                <td>{{ totalcv }}</td>
                <td>{{ totalav }}</td>
            </tr>            
        </table>
    </div>
</template>

<style lang="scss">
    table {
        border-collapse: collapse;
        margin-left: auto;
        margin-right: auto;
        text-align: center;
    }
    input {
        width: 50px;
        float: left;
    }
    th {
        border: 1px solid black;
        padding: 5px;
    }
    td {
        border: 1px solid black;
        padding: 5px;
    }
    .tables {
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
    }
    .small {
        min-width: 30px;
        max-width: 30px;
    }
</style>
