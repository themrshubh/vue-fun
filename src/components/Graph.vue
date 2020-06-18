<script>
import { Line } from 'vue-chartjs';

export default {
  mixins: [Line], 
  props:['chartData', 'options'],
  mounted (){
    console.log('Rendering..')
    this.renderChart(this.chartData, this.options)
  }
}
</script>

<style scoped>

</style>