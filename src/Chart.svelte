<script>
  import { Pie } from "svelte-chartjs";
  export let data = {};

  import { Chart as ChartJS, Title, ArcElement, CategoryScale } from "chart.js";

  ChartJS.register(Title, ArcElement, CategoryScale);
</script>

<Pie {data} options={{ responsive: true }} />
