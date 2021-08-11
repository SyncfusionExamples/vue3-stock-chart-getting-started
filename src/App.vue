
<template>
  <ejs-stockchart
    :primaryXAxis="primaryXAxis"
    :primaryYAxis="primaryYAxis"
    :title="title"
  >
    <e-stockchart-series-collection>
      <e-stockchart-series
        :dataSource="seriesData"
        type="Candle"
        volume="volume"
        xName="date"
        low="low"
        high="high"
        open="open"
        close="close"
        yName="open"
      ></e-stockchart-series>
    </e-stockchart-series-collection>
  </ejs-stockchart>
</template>

<script>
import {
  StockChartComponent,
  CandleSeries,
  DateTime,
  StockChartSeriesCollectionDirective,
  StockChartSeriesDirective,
  StockChart
} from "@syncfusion/ej2-vue-charts";
import { data } from "./datasource";
import { createApp } from "vue";

StockChart.Inject(CandleSeries, DateTime);

const app = createApp({
  // Displays "Hello, World" initially, changes based on input
  template: '<app></app>'
}); 

// Register the `hello` component
var itemVue = app.component('itemTemplate', {
  data: () => ({}),
});  
 
export default {
  name: "App",
  components: {
    "ejs-stockchart": StockChartComponent,
    "e-stockchart-series-collection": StockChartSeriesCollectionDirective,
    "e-stockchart-series": StockChartSeriesDirective
  },
  data() {
    return {
      seriesData: data,
      primaryXAxis: {
        valueType: "DateTime"
      },
      primaryYAxis: {
        majorTickLines: { color: "transparent", width: 0 },
      },
      title: "AAPL Stock Price",
      itemTemplate:  function() {
        return { template: itemVue };
      }
    };
  },
};
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";

button {
  margin: 25px 5px 20px 20px;
}
</style>
