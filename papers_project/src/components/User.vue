<template>
    <div id="app" class="row">

        <h1>Calculadora de Investimentos</h1>

        <div class="col-md-6">
            <label for="selicAtual">SELIC Atual: <b>12,25%</b></label>            
        </div>

        <div class="col-md-6">
            <label for="taxaSelic">Taxa SELIC / DI (anual): <b>12,15%</b></label>            
        </div>

        <div class="form-group">
            <label for="cdi">CDI (em %):</label>
            <input type="number" class="form-control" v-model="cdi" id="cdi">
        </div>

        <div class="col-md-6">
            <label for="investimentoInicial">Investimento Inicial (em R$):</label>
            <input type="number" class="form-control" v-model="investimentoInicial" id="investimentoInicial">
        </div>

        <div class="col-md-6">
            <label for="tempoInvestimento">Tempo de Investimento (Anos):</label>
            <input type="number" class="form-control" v-model="tempoInvestimento" id="tempoInvestimento">
        </div>

        <div class="form-group">
            <label for="tipoInvestimento">Tipo de Investimento</label>
            <select class="form-control" v-model="tipoInvestimento" id="tipoInvestimento">
            <option value="CDB">CDB</option>
            <option value="LCI">LCI</option>
            </select>
        </div>
    
        <button class="btn btn-primary" @click="calcular">Consultar</button>

        <!-- Resultados -->
        <div v-if="mostrarResultados">
            <h4>Resultados:</h4>
            <p>Total Bruto: R$ {{ formatarNumero(totalBruto) }}</p>
            <p>Rendimento Parcial: R$ {{ formatarNumero(rendimentoParcial) }}</p>
            <p>IR: R$ {{ formatarNumero(ir) }}</p>
            <p>Rendimento Líquido: R$ {{ formatarNumero(rendimentoLiquido) }}</p>
            <p>Total Líquido: R$ {{ formatarNumero(totalLiquido) }}</p>
            <p>Aumento de Patrimônio: % {{ formatarNumero(aumentoPatrimonio) }}</p>
        </div>
    </div>

  </template>
  
<script>
    export default {
        name: 'Simulador',    
        data() {
            return {
                mostrarResultados: false,
                totalBruto: '',
                rendimentoParcial: '',
                ir: '',
                rendimentoLiquido: '',
                totalLiquido: '',
                taxaIR: '',
                investimentoInicial: '',
                tipoInvestimento: '',
                tempoInvestimento: '', 
                cdi: '',
                aumentoPatrimonio: ''
            };
        },
        methods: {
            calcular() {
                this.mostrarResultados = true; 
                this.calculoTotalBruto();    
                this.calculoRendimentoParcial();                
                this.calcularIR();
                this.calculoRendimentoLiquido();
                this.calculoTotalLiquido();
                this.calculoPatrimonio();
            },
            calculoTotalBruto() {                
                this.totalBruto = this.investimentoInicial * Math.pow((1 + ((12.15 / 100) * (this.cdi / 100))), this.tempoInvestimento);
            },
            calculoRendimentoParcial(){
                this.rendimentoParcial = this.totalBruto - this.investimentoInicial; 
            },            
            calcularIR() {
                if (this.tipoInvestimento === 'LCI') {
                    this.ir = 0.00;
                }

                else if (this.tipoInvestimento === 'CDB') {

                    if (this.tempoInvestimento > 1) {
                        this.taxaIR = 0.15;
                    }

                    else if (this.tempoInvestimento === 1) {
                        this.taxaIR = 0.175;
                    }

                    this.ir = this.rendimentoParcial * this.taxaIR;
                }
                
            },
            calculoRendimentoLiquido(){
                this.rendimentoLiquido = this.rendimentoParcial - this.ir;
            },
            calculoTotalLiquido(){
                this.totalLiquido = this.investimentoInicial + this.rendimentoLiquido;
            },
            formatarNumero(numero) {
                return parseFloat(numero).toFixed(2);
            },
            calculoPatrimonio() {
                this.aumentoPatrimonio = ((this.totalLiquido - this.investimentoInicial) / this.investimentoInicial) * 100;
            }
        }
    } 
</script>
  
<style scoped>
    .form-group {
        width: 500px;       
        margin: auto; 
    }

    .row {
        width: 500px;
        margin: auto;      
    }

    td {
        text-align: center;
        vertical-align: middle;
    }

    label {              
        margin-bottom: 5px;
        margin-top: 5px;
        color: #222;        
        border-left: 4px solid #FCBA03;
        width: 500px;
        text-align: left;
        padding: 8px;      
    }

    input {
        margin-bottom: 10px;
    }

    button, h4 {
        margin-top: 10px;
    } 
</style>
  